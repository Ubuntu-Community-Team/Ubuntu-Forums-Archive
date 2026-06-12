---
title: "Little Help Getting Started"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Etheredge on 2008-04-20
Well hello first off and i think this will be one of many posts to these forums. Hopefully in the near future i am able to get myself outa the newb section....

Anyways here is the problem. 

Im not to familiar with the process of installing programs with ubunto much less any other linux based system

Im trying to get the Gnome Im program to be installed but when i go to the <add remove programs> and i click on the Gnome Im program it keeps telling me i need to refresh the screen before i can do anything...

Any ideas? or general help tips at all would be very helpful.

---

### Post by cardinals_fan on 2008-04-20
If it tells you to refresh, let it refresh.  Then search for your app.

---

### Post by joshrobinson on 2008-04-20
click applications > accessories > terminal
type
```
sudo apt-get update
```
and enter your password

when its done try using add/remove programs to install it again

---

### Post by Afkpuz on 2008-04-20
The gnome IM application?  Have you tried pidgin?  goto Applications>Internet>Pidgin

Pidgin is the default IM client and comes installed with ubuntu.  check it out!

---

### Post by Etheredge on 2008-04-21
Well i took a screen shot of the message that it keeps telling me but photo bucket wont seem to let me browse my computer to find the file to put it on the net.... So.....

here it is...

[B]"The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection."[/B]

It keeps coming up even after i did the above steps.

Thanks for the quick replies btw

and before someone asks of im using the same computer to be on the forum so yes my internet is fine

---

### Post by erginemr on 2008-04-21
As said above, you should go for **Pidgin** first. It is pretty powerful and versatile supporting quite a few chat protocols. If you are looking for an MSN clone, you can also try **aMSN** and **emesene**.

---

### Post by SunnyRabbiera on 2008-04-21
hmm, well it could be your repository mirrors.
where are you and what kind of connection are you using?

---

### Post by erginemr on 2008-04-21
Hmm, it seems when you installed your system, internet was not working, so the system has disabled your software repositories. 

Please go to Menu -> System -> Admin -> Software Repositories and enable main, universe, restricted and multiverse repositories, while disabling Ubuntu CD-ROM as a software repository.

---

### Post by Etheredge on 2008-04-21
> Hmm, it seems when you installed your system, internet was not working, so the system has disabled your software repositories.

Please go to Menu -> System -> Admin -> Software Repositories and enable main, universe, restricted and multiverse repositories, while disabling Ubuntu CD-ROM as a software repository.

Thank you very much it worked quite well : )

---

