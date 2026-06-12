---
title: "/etc/x11/x is not executable"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-09-08
so
this is what i get when I try to log on.... very confusing to a n00b like me!

what is the solution? All I know is what I got next which was

[PHP]The X server is now disabled[/PHP].

[PHP]Restart GDM when it is configured correctly.[/PHP]

What is to be done?

I have my wife's laptop for about one more hour, tehn she leaves on business trip... and I will be without a way to check the forum.

thanks for the help in advance.

robi

---

### Post by diatribe on 2007-09-08
[http://ubuntuforums.org/archive/index.php/t-36392.html](http://ubuntuforums.org/archive/index.php/t-36392.html)

---

### Post by bodhi.zazen on 2007-09-08
I am not so sure about that link ...

Have you done anything to change X ? Install a new video driver ? configure Beryl/Compiz ?

Otherwise check you logs (click OK and vew the output)

Otherwise ctrl-alt-F2, log in, cd /var.log

now less /var/log/Xorg.0.log

post that file ...

---

### Post by beanco on 2007-09-08
i have made no changes, no installations, etc other than changing my sons resolution yesterday...

BTW I am still in dapper...

i will try your commands and post the results.


thanks

robi

---

### Post by bodhi.zazen on 2007-09-08
Ah, probably a mis configuration in resolution then.

You can try :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Use the arrow keys and space bar to select the resolution you like, 

Restart X with :

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

/etc/init.d/gdm restart does not always work

You may need to Ctrl-alt-F7 to the gui

---

### Post by beanco on 2007-09-08
BZ, 

I am a total n00b... i tried your first suggestion and got no such directory or sg to that affect....

I typed in 

cd /var.log

i will try your other suggestions in a minute

robi

---

### Post by beanco on 2007-09-08
> **bodhi.zazen said:**
> Ah, probably a mis configuration in resolution then.

You can try :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Use the arrow keys and space bar to select the resolution you like, 

Restart X with :

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

/etc/init.d/gdm restart does not always work

You may need to Ctrl-alt-F7 to the gui


X servewr is not fully installed or sg like that is what I got!!!

robi

---

### Post by bodhi.zazen on 2007-09-08
Hmm, that seems odd ...

Can you try to post the exact error message ?

---

### Post by beanco on 2007-09-08
well, it's really long

but

here you go

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
Language  = "en_AU:en",
LC_ALL = (unset),
LANG =en_AU.UTF-8"

are supported and sintalled on your system.

perl: warning: falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory /usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed

---

### Post by diatribe on 2007-09-08
you're sure all you did was change the resolution?  I have never seen this error before

---

### Post by bodhi.zazen on 2007-09-08
I do not know that error either, but I found a link :

[http://ubuntuforums.org/showthread.php?t=75493](http://ubuntuforums.org/showthread.php?t=75493)

[http://mail-index.netbsd.org/tech-pkg/2002/12/03/0012.html](http://mail-index.netbsd.org/tech-pkg/2002/12/03/0012.html)

Not sure how this relates to xorg though ... ???

---

### Post by beanco on 2007-09-08
yeah, all i did was change his resolutin yesterday!

today it worked fine for a few hours, then went blitz on me...

i did try to update the repositroies but that should not have caused this...

robi

---

### Post by beanco on 2007-09-09
hi guuys
\anybody have any other ideas what I should do?

when logging on to try to earlier suggestions again i noticed this error msg

Configuration error - unknown item 'FAIL_DELAY' (notify administrator)

is this related to my original problem or sg elswe?

thanks

---

