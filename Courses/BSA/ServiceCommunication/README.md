# ServiceCommunication

### Що нового?

* проект **QueueService** — абстракція над RabbitMQ
* проект **FileWorker** 
    * отримує повідомлення із сервера, про те який метод викликаний
    * сереалізує дані у файл
    * сповіщає сервер про завершення сереалізації
* у проекті **Core** в папці **DataTransferObjects** додана папка **RabbitMQ** із даними, що транспортуються між проектами
* у проекті **ProjectStructure** (проект сервера)
    * папка **Filters** із класом-фільтром, який надсилає дані FileWorker'у про виклик метода
    * папка **HostedServices** із класом-сервісом, який асинхронно отримує від FileWorker'а дані про стан сереалізації
    * папка **Hubs** для налаштування зв'язку між клієнтом і сервером за допомогою WebSocket
    * в папці **Controllers** клас-контроллер **FileController** який, повертає на запит користувача вміст файлу із даними від FileWorker'а
* у проекті **BusinessLayer** в папці **Queries** додані хендлери
* у проекті **Client** (проект клієнта)
    * доданий сервіс **IFileService**, який вміє звератись до сервера і отримувати дані
    * доданий серів **IMessageService**, який сповіщає, про отримані резульати сереалізації від SignalR

### Запуск 

* відкриваємо за допомогою Visual Studio і будуємо
* після цього відкриваємо консоль (win + R, "cmd") за допомогою команди ``cd path\to\project`` відкриваємо папку проекта і запускаємо проект командою ``dotnet run``. Запускати проекти в такому порядку:
    * ProjectStructure — проект сервера
    * FileWorker
    * запускаємо через студію проект Client