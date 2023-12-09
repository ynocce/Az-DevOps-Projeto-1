# Como criar uma Release e fazer Deploy em um App Service.

Essa documentação tem como objetivo, orientar e mostrar passo-a-passo, como criar uma pipeline/release e fazer um deploy em um App Servicem, utilizando o Azure DevOps.

- Criando uma Pipeline Classic Editor
    
    Primeiro acessamos o Azure DevOps.
    
    Nesse caso, gerei uma build .NET, atráves do Visual Studio e mandei para meu repos no Azure DevOps.
    
    1 - Clique em Pipelines 
    
    2 - Clique em Create Pipeline.
    
    3 - Depois escolha como você deseja criar seu pipeline, yaml ou Editor Classico. (Nesse caso vamos criar por editor Classico)
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled.png)
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%201.png)
    
    4 - Podemos selecionar varios repos, Azure Repos, GitHub e etc. Mas nosso código está no Azure Repos.
    
    - Agora temos que selecionar nosso projeto.
    - O repositorio que vamos utilizar.
    - E nossa branche com o código mais atual.
    
    5 - E clicamos em continue
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%202.png)
    
    6 - Podemos criar um Empty Job (um job em branco, sem nada) ou usar um template
    7 - Nesse caso vamos usar um template, **ASP.NET**
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%203.png)
    
    8 - E assim está criado nosso build Classic Editor
    
    - Temos nosso Agent Job
    - Nossas tasks
    - Nosso agent e s.o que vamos rodar
    
    9 - Clique em Save & Queue
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%204.png)
    
    10 - Pipeline finalizada
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%205.png)
    
- Conectando o Azure DevOps com o Azure Portal.
    
    1 - Acessamos nosso projeto no Azure DevOps.
    
    2 - Clique em **Project Settings** e depois clique em **Service Connections.**
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%206.png)
    
    3 - Clique em New Service connection e selecione o **Azure Resource Manager.**
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%207.png)
    
    4 - Selecione como automatico e clique em **next.**
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%208.png)
    
    5 - Agora vamos criar a Service connection.
    
    Nota: Como minha conta Azure DevOps e Azure portal, utlizam o mesmo E-mail, ele já trouxe minha Subscription.
    
    1. Marque a opção **Subscription.**
    2. Ira abrir uma tela para logar com sua conta Microsoft, logue nela para trazer os recursos.
    3. Selecione a subscription que ele trouxe.
    4. Selecione o Resource Group que você deseja.
    5. Coloque um nome na sua Service connection e clique em Save.
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%209.png)
    
- Criando um App Service no Azure Portal.
    
    1 - Acesse o portal do Azure e pesquise por: App Service
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2010.png)
    
    2 - Clique em Criar → Aplicativo Web.
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2011.png)
    
    3 - Criando um App Service.
    
    1. Selecionamos nossa Subscription e Resource Group, igual no Azure DevOps
    2. Coloque um nome para o App Service.
    3. Como nossa aplicação é .NET, selecione .NET (STS)
    4. Nossa região será a  East US, por conta do custo.
    5. Selecione o Plano (nesse caso criei um para usar gratuitamente)
    6. Plano de preços
    7. Clique em revisar + Criar
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2012.png)
    
    4 - Pronto nosso App Service está criado.
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2013.png)
    
- Criando uma Release no Azure DevOps.
    
    1 - Vá para o Azure → Pipelines → Releases
    
    2 - Clique em Create Release → Azure App Service.
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2014.png)
    
    3 - Clique em Artifacts → Add
    
    1. Selecione Build → Projeto
    2. Selecione a nossa Build que ira gerar o artefato.
    3. Clique em Add
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2015.png)
    
    4 - Clique no Stage → 1 job, 1 task
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2016.png)
    
    5 - Configurando nossa release.
    
    1. Clique em Stage 1
    2. Selecione sua Azure Subscription (A mesma que está nosso recurso)
    3. Marque Web App on Windows
    4. Selecione nosso App service name (que criamos no Azure portal)
        
        ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2017.png)
        
    5. Clique em Run On agent
    Selecione o Agent Pool.
    Agent Specification.
    Selecione o Artefato.
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2018.png)
    
    6 - Clique na Task de Deploy Azure App Service e verique se as informações da task estão corretas.
    
    - Em package or folder, selecione os arquivos dentro do Artefato, no caso os **Zip.**
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2019.png)
    
    7 - Vá para a tela de pipeline e clique o raio que está no nosso artefato e clique em Enabled conforme imagem.
    Essa opção fara com que, após rodar nossa build Pipeline, fara com que dispare a release automaticamente, criando nosso Deploy automatizado. 
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2020.png)
    
    8 - Agora vá para pipelines e clique em **Run pipelines.** Após a conclusão da pipeline, ela ira disparar a release.
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2021.png)
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2022.png)
    
    9 - Acessando a parte de releases, ira verificar que a mesma está rodando sozinha, após o build finalizar.
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2023.png)
    
    10 - Agora acesse o Azure portal → App Service → Seu app service → Domínio padrão.
    Pronto foi realizado nosso Deploy e o mesmo já está funcionando
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2024.png)
    
    11 - Pronto, feito o deploy da nossa aplicação.
    
    ![Untitled](Como%20criar%20uma%20Release%20e%20fazer%20Deploy%20em%20um%20App%20Se%20cd57e244275e40c692e55fa2f8fb6315/Untitled%2025.png)
    
    Agora sempre que você fizer alguma alteração na aplicação, rode o build, assim ele dispara a nossa release, que ira fazer o Deploy em seguida.
