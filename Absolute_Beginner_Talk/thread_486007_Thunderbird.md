---
title: "Thunderbird"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Pizarro on 2007-06-27
I've just installed Thunderbird for my hotmail acccount..It works fine in windows but i can't get it to work in ubuntu.  I get the message "could not connect to server local host; the connection was refused"

---

### Post by Seisen on 2007-06-27
Do you have pop access through hotmail?

---

### Post by technikalKP on 2007-06-27
Are you using the Web-Mail extensions?  If so, set the ports to something higher than 1000.  I believe they default to 25 to SMTP and 110 for POP.  I changed mine to 1025 and 1110 respectively and that solved the problem.  Ubuntu seems to block ports below 1000.

You can access the port settings in the Web-Mail add-on.  You'll then need to change the Account settings under Thunderbird for both your Hotmail account and the Localhost SMTP account to match what you set in the add-on.

---

### Post by Pizarro on 2007-06-27
Ports it is . I set them in webmail to POP 1200 and SMTP 1250, adjusted accounts accordingly and it all works.:D:D:D:D:D

---

### Post by stchman on 2007-06-27
> **Pizarro said:**
> I've just installed Thunderbird for my hotmail acccount..It works fine in windows but i can't get it to work in ubuntu.  I get the message "could not connect to server local host; the connection was refused"

I am wanting to get hotmail email on my Evolution email client.

Do you pay Hotmail for pop access?

---

### Post by Inxsible on 2007-06-27
If you use Thunderbird, you can install WebMail add on which allows web based email to be seen in Thunderbird client.
 
I dont think Evolution has anything like that

---

### Post by Seisen on 2007-06-27
> **stchman said:**
> I am wanting to get hotmail email on my Evolution email client.

Do you pay Hotmail for pop access?

As far as I know you have to pay for hotmail pop access but their are programs that act like a pop server for hotmail.

This guide might help you

[http://ubuntuforums.org/showthread.php?t=200408]("http://ubuntuforums.org/showthread.php?t=200408")

---

