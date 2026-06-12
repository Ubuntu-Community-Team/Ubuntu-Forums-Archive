---
title: "New to Linux, Graphical Server?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by M374llic4 on 2006-09-12
Hello everyone,

    I am sorry, and am sure this has been discussed before, but I am at work and can not do alot of searching. 

    Is it possable to have a full featured desktop on the server installation of Ubuntu, would you download the desktop version and add the server applications to it? I would like the full functionality of both in one. 

Any help would be most appreciated : ) I will be sure to do more searching later, as I am still quite a noob and accidently wrote over my windows installation last night, though that was probably for the best. haha.

---

### Post by Ripfox on 2006-09-12
Whatever you do...go with it. Friends don't let friends reinstall XP. =D>

---

### Post by Iarwain ben-adar on 2006-09-12
Hi,
first of all, welcome to the forums :D

Now, you have to know that a desktop installation is just a server installation with a graphical server on top of that ;)

So if you would like Gnome, type this
```
sudo aptitude install ubuntu-desktop
```

If you'd like KDE
```
sudo aptitude install kubuntu-desktop
```

And if your willing to try Xfce
```
sudo aptitude install xubuntu-desktop
```

You can just install all three if you can't decide :D
```
sudo aptitude install ubuntu-desktop kubuntu-desktop xubuntu-desktop
```


Iarwain

---

### Post by evolvedlight on 2006-09-12
Hey

It is possible to install a desktop environment onto the server version - just type ```
sudo apt-get install ubuntu-desktop
```

I would not do this, however, I would install the normal version and add the server software onto it.

If you want Apache (the most popular webserver) follow this guide:

[http://ubuntuguide.org/wiki/Dapper#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Dapper#Apache_HTTP_Server)

Then, put your files inside /var/www/ to see them on your webserver (you can find it at [http://localhost/](http://localhost/)

You may need to change the permissions of the directory /var/www/ to be able to place your files into it.

To do this, go to terminal and type "sudo chmod 777 /var/www/

If you have any more questions, feel free to ask

Steve

Edit: Dah! Beaten to the post! Curse my slow typing!

---

### Post by M374llic4 on 2006-09-12
> **Iarwain ben-adar said:**
> Hi,
first of all, welcome to the forums :D

Now, you have to know that a desktop installation is just a server installation with a graphical server on top of that ;)

So if you would like Gnome, type this
```
sudo aptitude install ubuntu-desktop
```

If you'd like KDE
```
sudo aptitude install kubuntu-desktop
```

And if your willing to try Xfce
```
sudo aptitude install xubuntu-desktop
```

You can just install all three if you can't decide :D
```
sudo aptitude install ubuntu-desktop kubuntu-desktop xubuntu-desktop
```


Iarwain
 wow : ) Nice to see a forum where you arent jumped on and flamed for not knowing something. : ) I can already see I will like it here.

So the server install includes the graphical attributes, but they are just not installed? Its good to get the server version, then load up the graphical packages over it?

The last post said its better to get the graphical, then add server software to it?

Is it more a preference thing? Which would be easier. I have 56k at home right now, so I have to download everything at work, and need the easiest way to go about it, but most effective.


Thanks again for the help : )

---

### Post by Iarwain ben-adar on 2006-09-12
Hi,
no problem :D

But i do think that the last post was a bit more correct than me (i don't know that much)

If you're not going to download via aptitude, it is quite the hassle i think, because of all the dependencies... :-/


Iarwain

---

### Post by M374llic4 on 2006-09-12
> **Iarwain ben-adar said:**
> Hi,
no problem :D

But i do think that the last post was a bit more correct than me (i don't know that much)

If you're not going to download via aptitude, it is quite the hassle i think, because of all the dependencies... :-/


Iarwain


I need to do some more reading I guess while I try to do this because I didnt get most of what you just said : \

As well as figuring out how to do this, any good tutorials you could recommend?

I really want full functionality of both packages, because I am trying to learn everything I can about linux, as I hope to go back to school soon for system administration and network engineering.

That and windowz just sucks >_< 

So then its better to get the graphical version then install the server software? How do you know exactly what all software it has that the graphical doesnt have? They should have an upgrade package for the server edition that gives all the functionality of the desktop version.

---

### Post by Iarwain ben-adar on 2006-09-12
Hi,
i don't know any tutorials, sorry (learned the most of trying to repair my pc :D )

I heard something of an other cd (?alternate?), and that could help you easily install most of the stuff you would need to download...
BUT don't quote me on that! (i only heard of it)


Iarwain

---

### Post by Iarwain ben-adar on 2006-09-12
double post


Iarwain

---

