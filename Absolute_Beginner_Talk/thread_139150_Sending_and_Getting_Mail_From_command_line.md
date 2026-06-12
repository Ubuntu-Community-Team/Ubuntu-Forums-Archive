---
title: "Sending and Getting Mail From command line"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by utab on 2006-03-03
Dear all,

Could somebody tell me how to use the command line to write read and send mails? I tried sendmail command but it can not be found nor the fetchmail command.

Thanks in advance.

---

### Post by Pragmatist on 2006-03-03
have you tried ```
sudo synaptic
``` and search for sendmail?  I'm running  Breezy and I've got sendmail installed by default.

---

### Post by soce_32 on 2006-03-03
Mutt and pine are probably the most feature-rich terminal mailers around.  Pine has a restrictive license and you will have to activate universe or multiverse to get it.

If you are looking for something more basic, mailx will do command-line actions without having to open a client like mutt or pine.

---

### Post by carlossousa on 2006-11-07
Hello there,

Isn't it possible to send mail in the form of a script? In the likes of 
$mail "some text" to "someone@somewhere" from "root@computer"
??

Thanks

---

### Post by LadyDoor on 2006-11-07
[quote=carlossousa]
Isn't it possible to send mail in the form of a script? In the likes of                                                                     
$mail "some text" to "someone@somewhere" from "root@computer"
[/quote]

I believe so. If you read the manpage of **mail** (which may be in
the package **mailutils**), I think you'll find instructions on
doing that.

[quote=Pragmatist]
have you tried                                                                                                                              
```
$ sudo synaptic
```
and search for sendmail? I'm running Breezy and I've got sendmail
installed by default.
[/quote]

This is a good suggestion, but some notes for future reference:

(1) It's appropriate to use gksudo or kdesu in lieu of sudo to launch
    a graphical application--sudo is for nongraphical applications.

(2) For a user who prefers the console, I would suggest that they use
    **aptitude** (a console-based frontend to APT) or [b]apt-cache
    search[/b] to search for packages and [b]sudo aptitude install
    packagename[/b] (or **sudo apt-get install packagename**) :-)

[quote=utab]
Could somebody tell me how to use the command line to write read and
send mails? I tried sendmail command but it can not be found nor the
fetchmail command.
[/quote]

First, enable the Universe repository (instructions can be found
elsewhere on the Forums and in the Wiki). Then...

```

$ sudo apt-get update
$ sudo aptitude install sendmail fetchmail mailutils

```

Now check out the mail command (for pure commandline), mutt for a very
configurable and powerful but learnable MUA, gnus/vm/wl/etc. if you're
an Emacs user *already*, or google for something along the lines
of console email to find other MUAs/mailreaders.

I hope that was helpful...

--Door

---

### Post by Pragmatist on 2006-11-07
> **carlossousa said:**
> Hello there,

Isn't it possible to send mail in the form of a script? In the likes of 
$mail "some text" to "someone@somewhere" from "root@computer"
??

What exactly do you want the script to do?  A script can use, among other things, any shell commands.  So, since you can mail from the command-line using the **mail** command, you can write a script to automate anything you would normally type from the console.

If your just trying to send a message to one or more people then, according to the manpage, you do this:

>  To send a message to one or more people, **mail** can be invoked with arguments which are the names of people to whom the mail will be sent. You are then expected to type in your message, followed by an `**control-D** ' at the beginning of a line. The section below *Replying to or originating mail* describes some features of **mail** available to help you compose your letter.If this is all you want to do, a script isn't useful. Unless, you have a file containing a list of names you want the mail sent to.  Then you can use a script to read the names in as arguments rather than type them in yourself.  Of course, if there is something more complex you are trying to do, then a script might be helpful.

What are you trying to do?

---

### Post by andrew.46 on 2007-07-16
Hi,

 Raed your post:

> **utab said:**
> Dear all,

Could somebody tell me how to use the command line to write read and send mails? I tried sendmail command but it can not be found nor the fetchmail command.

Thanks in advance.

 Sounds like you need mutt:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

                  Andrew

---

