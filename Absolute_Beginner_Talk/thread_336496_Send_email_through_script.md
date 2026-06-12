---
title: "Send email through script"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-01-11
I've been trying for a while to set up a way to send emails from a perl script or even the terminal. Currently, I use thunderbird to send email. It uses my gmail account and smtp.gmail.com to send the mail. smtp.gmail.com requires all these authentication things to work ([http://mail.google.com/support/bin/answer.py?answer=13287&topic=1556)](http://mail.google.com/support/bin/answer.py?answer=13287&topic=1556)). Is there any way I can connect to smtp.gmail.com to send mail from the perl script/terminal? I don't need to be able to read mail, just send it. If I could send from an email account other than my own (without making a new account), that would be even better. I have a feeling that will involve a different smtp server, which is fine, as long as it works.

---

### Post by Ecthelion on 2007-01-13
I have [a link]("http://www.cyberciti.biz/tips/sending-mail-with-attachment.html") here for a terminal command to send emails.

Is this what you are looking for?

---

### Post by Ecthelion on 2007-01-13
>    | **Internet site** - mail is sent and received directly using SMTP. If your    
 &#9474; needs don't fit neatly into any category, you probably want to start      
 &#9474; with this one and then edit the config file by hand.                      
 &#9474;                                                                           &#9646;  
 &#9474; **Internet site using smarthost** - You receive Internet mail on this         
 &#9474; machine, either directly by SMTP or by running a utility such as          
 &#9474; fetchmail. Outgoing mail is sent using a smarthost. optionally with     
 &#9474; addresses rewritten. This is probably what you want for a dialup system. 
  |  **Satellite system** - All mail is sent to another machine, called a "smart   
 &#9474; host" for delivery.  No mail is received locally.                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; **Local delivery only** - You are not on a network.  Mail for local users is  &#9646;  
 &#9474; delivered.        

Small part of the configuration...

Just try it out, configure it, and tell us if it worked for you...

---

### Post by souki on 2007-01-13
gmail uses smtp over ssl
so, I think you should use the Net::SMTP::SSL module

---

### Post by KeithEckstein on 2007-01-13
Cheater

I don't know if this is what you are after but I send mail to a Gmail account as part of my nightly backup process - I use MUTT to do this.

The relevant portion of the backup script is as follows...

# And now Mail it to [email]Mozart.Archive@Gmail.com[/email]
[I]mutt -s "MailBack" -a /home/keckstein/Data/Tars/MailBack.tar.gz [email]MozartArchive@Gmail.com[/email] < backuplog.000 
[/I]
I can obviously do the same thing from the console without having to run it in a script.

Hope this helps

Keith (learning a little more, every day)

---

### Post by speedman on 2007-01-13
[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

SM

---

### Post by Ecthelion on 2007-01-13
> I don't know if this is what you are after but I send mail to a Gmail account as part of my nightly backup process - I use MUTT to do this.

:mrgreen: 

The link I posted previously was to a page where was explained how to install & use MUTT :-D

Note to myself: say to where a posted link goes 8)


To be quite honest, I'm glad someone else recommends it... I just googled for a prog that could be used to send emails using Script/Command-line.
But as I tested it myself it didn't worked...

When I first installed it it asked me to choose one of these
>  | Internet site - mail is sent and received directly using SMTP. If your
&#9474; needs don't fit neatly into any category, you probably want to start
&#9474; with this one and then edit the config file by hand.
&#9474; &#9646;
&#9474; Internet site using smarthost - You receive Internet mail on this
&#9474; machine, either directly by SMTP or by running a utility such as
&#9474; fetchmail. Outgoing mail is sent using a smarthost. optionally with
&#9474; addresses rewritten. This is probably what you want for a dialup system.
| Satellite system - All mail is sent to another machine, called a "smart
&#9474; host" for delivery. No mail is received locally. &#9618;
&#9474; &#9618;
&#9474; Local delivery only - You are not on a network. Mail for local users is &#9646;
&#9474; delivered.

However, I think I choosed wrong and configured it wrongly.
Does one of you know how I could reconfigure it using the menus that appeared then?

Reinstalling etc doesn't work #-o


Also, could you tell how you configured it to work with your gmail?


[EDIT]
Nevermind, tried sendemail and that worked fine.
[/EDIT]

---

### Post by nhandler on 2007-01-14
Thank you for all the suggestions. Currently, I am on vacation, and I do not have access to my linux box. I will try these out when I get back.

---

### Post by nhandler on 2007-01-15
> **speedman said:**
> [http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

SM

That program worked perfectly. Now, I just need to remember how to execute terminal commands from within a perl script.

---

### Post by souki on 2007-01-16
with perl, you can use back-quotes :
> `the_shell_command args`;

---

### Post by nhandler on 2007-01-16
> **souki said:**
> with perl, you can use back-quotes :
I never new that before. That's pretty cool.

---

