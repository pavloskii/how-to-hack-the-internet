# how-to-hack-the-internet

    class Program
    {
        const string API_KEY = "";

        static void Main(string[] args)
        {
            var sendGridClient = new SendGridClient(API_KEY);

            var fromMail = new EmailAddress("got@hacked.com");
            var toMail = new EmailAddress("bale7.7@hotmail.com");
            var subject = "More apo apo apo zs ne dojde";
            var plainText = "Si prajme muabet";
            var htmlText = "<b>OOOO more Blagojce</b>";
            var message = MailHelper.CreateSingleEmail(fromMail,toMail,subject,plainText,htmlText);

            var bytesContent = File.ReadAllBytes(@"Files\BlagojceOdOhridSoNeDojde.txt");
            var stringContent = Convert.ToBase64String(bytesContent);
            message.AddAttachment("BlagojceOdOhridSoNeDojde.txt", stringContent);

            var response = sendGridClient.SendEmailAsync(message).GetAwaiter().GetResult();

            Console.WriteLine(response.StatusCode);
        }
    }
