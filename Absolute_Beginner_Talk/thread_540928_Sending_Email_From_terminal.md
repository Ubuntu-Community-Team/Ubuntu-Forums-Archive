---
title: "Sending Email From terminal"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-09-02
yesterday i was learning shell commands and came [across this ]("http://rute.2038bug.com/node13.html.gz#SECTION001320000000000000000")
which showed how to send mail from terminal but i did not understand it well.  so anyone could tell me where could i find more information. 
(sending mail with a different name just thrilled me )

---

### Post by PmDematagoda on 2007-09-02
Brilliant find, this is really handy, i tried it just now you just need to change certain commands to fit your specifications, if you have Gmail it should be 
telnet smtp.gmail.com 25. Though I seem to have a problem establishing a TLS connection, does anyone know how to?

---

### Post by rahul_bhise on 2007-09-02
i don't have a gmail my isp is dataone in India it has given me an email.it has mail receiving pop3 and and mail sending smtp (i dont know anything of this i only have to put this data in appropriate places while configuring my evolution mail)

---

### Post by Koybe on 2007-09-02
You should use the mail command which is in the mailx package to send a mail trough the command line. Here's the man page : [http://unixhelp.ed.ac.uk/CGI/man-cgi?mail](http://unixhelp.ed.ac.uk/CGI/man-cgi?mail)

example : ```
mail -s "Subject for my mail" recipient@domain.org
``` then it will ask for CC, for the text to place in the mail. When you finished it a dot and it will send your mail.

Telnet is a way to contact a server on a specified port and talking with him. But to to this you need to know and/or understand the protocol you are using (in this case smtp).

[http://www.cyberciti.biz/faq/howto-write-command-to-send-receive-mail/](http://www.cyberciti.biz/faq/howto-write-command-to-send-receive-mail/)

---

### Post by Bachstelze on 2007-09-02
> **Koybe said:**
> You should use the mail command which is in the mailx package to send a mail trough the command line. Here's the man page : [http://unixhelp.ed.ac.uk/CGI/man-cgi?mail](http://unixhelp.ed.ac.uk/CGI/man-cgi?mail)

example : ```
mail -s "Subject for my mail" recipient@domain.org
``` then it will ask for CC, for the text to place in the mail. When you finished it a dot and it will send your mail.

Only if there's a MTA installed, which I doubt.

---

### Post by Skrynesaver on 2007-09-02
If you want to automate sending mail from an application/script then mail and sendmail are very useful, though as noted by Hymn to Life you do need to have an MTA (Mail Transfer Agent) such as Postfix Sendmail or Exim installed.  If however you are looking for a way of composing, reading and sending mail from the command line take a look at mutt and pine.

Mutt is more feature-full but takes a while to get the hang of.

---

### Post by ecoxmit on 2007-09-02
msmtp is quite easy to use, and easy to configure (it works with gmail also). After installing from synaptic, you only need to create a .msmtprc in your ~ directory. Mine is configure to send with gmail and reads:

```
account gmail
host smtp.gmail.com
auth on
user YOURGMAILADDRESS
password YOURPASSWORD
tls on
port 587
#tls_starttls on
from YOURGMAILADDRESS
maildomain gmail.com
account default : gmail
logfile /home/YOURHOME/.msmtplog

```

For general configurations, search the forums, i think it has been discussed here, (or google). 

An example of a command line usage: 

```
echo "subject: testing" | msmtp EMAILADDRESSHERE
```

---

### Post by ryanVickers on 2007-10-18
using mail, is there no way to set what the body is!?!? :shock: :mad:

---

### Post by andrew.46 on 2007-10-29
Hi,

I have been following this thread:

> **ryanVickers said:**
> using mail, is there no way to set what the body is!?!? :shock: :mad:

and thinking that while using mail has some novelty value surely you would *really* use a more fully featured console program such as mutt:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

BTW your avatar appears to have cut out one of it's eyes :confused:

                      Andrew

---

### Post by ryanVickers on 2007-10-29
> **andrew.46 said:**
> 
BTW your avatar appears to have cut out one of it's eyes :confused:

                      Andrew

it's just for Halloween ;)

---

