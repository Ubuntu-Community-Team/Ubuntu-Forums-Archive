---
title: "linux XGL"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by Sipheren on 2006-03-25
Hey,
I am trying to install this xgl stuff, I have updated Hoary to the latest Breezy (I think it worked anyway). I did this becasue when I follow that thread about installing I get to installing compiz-gnome thing and it cant find the package, I have added all the extra reposatorys and it still wont find it so I cant install xgl....

Does anyone know what I am doing wrong. I have only used Windows and am very new to Linux so I dont get how to do sertian things but am wanting to learn....:D 

thx


Sipheren

---

### Post by commodore on 2006-03-25
I wanted to use XGL and I too didn't find the packages. People from ubuntu chat said the packages are only available for dapper :(

You have only used Windows and you want to install XGL? It may be a bit hard for a newcomer I think.

---

### Post by Ubuntuud on 2006-03-25
I am running Breezy and XGL... It is quite easy, you are lucky if you have an i810 (or like me, a i810 driven card (like i915)). But assuming you don't you should combine the XGL/Compiz under Breezy tutorial with the ATI or NVidia one for Dapper.
But indeed, if you are a newcomer it is hard, but not impossible...

---

### Post by Thirion on 2006-03-25
I think the best way to get XGL is to try the [The Kororaa Xgl Demo Live CD ]("http://kororaa.org/static.php?page=static060318-181203"). 

If that work's you can download Dapper, install a second Ubuntu on another partition and try to get XGL working. But it's not easy and if you don't know Linux well you may get much problems (e.g GDM doesn't start)!

You should search the forum and get some information wether your system is supported or not (e.g. i have many problems with my ATI Radeon 9200SE).

---

### Post by Sipheren on 2006-03-27
ok, I have downloaded and installed ubuntu 5.10 and went through to install xgl...I get this message...can anyone tell me what I do to fix it?

[PIC]("http://img61.imageshack.us/my.php?image=screenshot8ow.png")

---

### Post by meborc on 2006-03-27
i don't understand... ](*,) if you are so keen in testing xgl... then you are probably the sort of a person, who really don't care if something happens to your data :mrgreen: ... by that i mean that you are willing to make a re-install of your sys...

so... why not upgrade to dapper... it is much easier to get the xgl working...

to upgrade:

**sudo gedit /etc/apt/sources.list**

change every **breezy **to **dapper **and **#** out the extra repostitories/backports

[B]sudo apt-get update
sudo apt-get dist-upgrade[/B]

[COLOR="DarkRed"]there are probably some problems[/COLOR], but you are willing to risk, aren't you :twisted: 

so join the dapper testing team... and locate all the xgl forums under [**dapper section**]("http://www.ubuntuforums.org/forumdisplay.php?f=111")

---

