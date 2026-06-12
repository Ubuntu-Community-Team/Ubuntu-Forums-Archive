---
title: "Moving to Xubuntu..."
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Brahman on 2006-09-10
I've deicided instead of putting more RAM in my PC right now I'll give Xubuntu a try. I like the way it looks in the screenshots. I think I'll give it a go...can I still get support in these forums for Xubuntu like Ubuntu? 


Oh and do all distros based off of Ubuntu have to have the buntu or part of its name in the new distros name? It seems they all do lol just curious. :D

---

### Post by electricshoes on 2006-09-10
Yeah, there are tons of people in the Ubuntu forums who use Xfce and would answer your questions.

Yeah, most do, Ubuntu is based off of Debian and all the ubuntu based distros have buntu in the name - Kubuntu, Xubuntu, Nubuntu, Edubuntu.

---

### Post by Brahman on 2006-09-10
But do they all have to have part of Ubuntu in their names? If someone made a new distro off on a Ubuntu or one of the based off distros of Ubuntu, is it a requirement to have part of Ubuntu in it? Seems so, thus far.


Also , is there a way to have the Xubuntu CDs shipped like Ubuntu does?

---

### Post by aysiu on 2006-09-10
They all have Ubuntu in the name because they're all produced by Canonical (the same company).

Other distros based on Ubuntu do not have to have Ubuntu in the name (for example, Mepis and ImpiLinux).

---

### Post by Najand on 2006-09-10
> **Brahman said:**
> I've deicided instead of putting more RAM in my PC right now I'll give Xubuntu a try. I like the way it looks in the screenshots. I think I'll give it a go...can I still get support in these forums for Xubuntu like Ubuntu? 


Oh and do all distros based off of Ubuntu have to have the buntu or part of its name in the new distros name? It seems they all do lol just curious. :D

They ship the Xubuntu CDs, too.... But it takes longer shippings... If you have Ubuntu CDs, then install UBUNTU and then use the command:
```
$ sudo apt-get install xubuntu-desktop
```
And xubuntu and all of its packages (even xubuntu splash) will be installed on your system.

---

### Post by bodhi.zazen on 2006-09-10
> **Brahman said:**
> I've deicided instead of putting more RAM in my PC right now I'll give Xubuntu a try. I like the way it looks in the screenshots. I think I'll give it a go...can I still get support in these forums for Xubuntu like Ubuntu? 


Oh and do all distros based off of Ubuntu have to have the buntu or part of its name in the new distros name? It seems they all do lol just curious. :D

Try icewm or fluxbox. Both are musch less resource intense then XFCE.

They will take some time to learn.

---

### Post by Najand on 2006-09-10
> **bodhi.zazen said:**
> Try icewm or fluxbox. Both are musch less resource intense then XFCE.

They will take some time to learn.

I use fluxbox...It is as light as a feather... Though setting is a pain in the *** at the begining.

---

### Post by bodhi.zazen on 2006-09-10
> **Najand said:**
> I use fluxbox...It is as light as a feather... Though setting is a pain in the *** at begining.

I wrote some how-to's which have been helpful to new (fluxbox) users. Check the link in my signature.

If you would be so kind....

Any feed back you may have would be appreciated as I anticipate working on a Fluxbox wiki. You can PM me at Ubuntu or fluxbuntu.

---

### Post by Brahman on 2006-09-10
> **Najand said:**
> They ship the Xubuntu CDs, too.... But it takes longer shippings... If you have Ubuntu CDs, then install UBUNTU and then use the command:
```
$ sudo apt-get install xubuntu-desktop
```
And xubuntu and all of its packages (even xubuntu splash) will be installed on your system.


I have the Ubuntu Cds coming in the mail already. So Xubuntu can be installed using the Ubuntu CD? Will the Xubuntu stuff replace the Ubuntu stuff?

---

### Post by Najand on 2006-09-10
> **Brahman said:**
> I have the Ubuntu Cds coming in the mail already. So Xubuntu can be installed using the Ubuntu CD? Will the Xubuntu stuff replace the Ubuntu stuff?

Yes, Xubuntu can be installed using the Ubuntu CD. Just by running the command above iit can be done easily. It will overwrite a few things like splash, but you can select the desktop environment at the login... So when you need gnome, just selecting it during login is enough.

---

### Post by Brahman on 2006-09-10
Can I install Xubuntu with only its desktop environment, not gnome, cuz my computer only has 128 MB of RAM and I was told I could get Xubuntu on it, but it'd still be slow until I have time to get more RAM.

---

### Post by Brahman on 2006-09-10
Oh and do I type that command in the terminal, if so I can't do that cuz Ubuntu won't even load becuase I only have 128 MB of RAM.

---

### Post by electricshoes on 2006-09-10
> **Brahman said:**
> Oh and do I type that command in the terminal, if so I can't do that cuz Ubuntu won't even load becuase I only have 128 MB of RAM.
 
Can you get to GDM the login screen? if so you can choose Session and use a failsafe terminal. Or not use a gui at all.

---

### Post by Brahman on 2006-09-10
No, just now it laoded and the two panels appeared, only white. 

It never goes to any login screen. So would it be better to just download Xubuntu and not install it off of Ubuntu CD?

---

### Post by electricshoes on 2006-09-10
So you dont have ubuntu installed yet, your booting from the CD ?
 
 Yeah if you want to you can download the Xubuntu cd, boot from it and run the installer, that should get you up and going. XFCE is super light.

---

### Post by Najand on 2006-09-10
If GDM  does not load, Push:
ALT+CTRL+F1
Login in pure command prompt.
And then use the apt-get command.

However 128MB is enoough to load gnome. Maybe you have some problems with  X settings... It may prevent you to load XFCE too.

---

### Post by bodhi.zazen on 2006-09-10
> **Brahman said:**
> Oh and do I type that command in the terminal, if so I can't do that cuz Ubuntu won't even load becuase I only have 128 MB of RAM.

To strat xfce from the cli
```
xfce4-session
```
if that is what you are now asking.

you do not need gnome to run xfce if that is what you are asking.

Otherwise I am not sure I understand.

---

### Post by Najand on 2006-09-10
> **bodhi.zazen said:**
> To strat xfce from the cli
```
xfce4-session
```
if that is what you are now asking.

you do not need gnome to run xfce if that is what you are asking.

Otherwise I am not sure I understand.

Well,  I think he has not installed XFCE yet. He need to install it first.

---

### Post by Brahman on 2006-09-11
> **Najand said:**
> If GDM  does not load, Push:
ALT+CTRL+F1
Login in pure command prompt.
And then use the apt-get command.

However 128MB is enoough to load gnome. Maybe you have some problems with  X settings... It may prevent you to load XFCE too.

I did that but when I typed in the apt-get command and hit enter it only went down to the next line and did nothing. Did I do something wrong?

---

### Post by Najand on 2006-09-11
> 
Quote:
Originally Posted by Najand View Post
If GDM does not load, Push:
ALT+CTRL+F1
Login in pure command prompt.
And then use the apt-get command.

However 128MB is enoough to load gnome. Maybe you have some problems with X settings... It may prevent you to load XFCE too.

I did that but when I typed in the apt-get command and hit enter it only went down to the next line and did nothing. Did I do something wrong?

What apt-get command did you use? The command I told you, before?
I mean
```

sudo apt-get install xubuntu-desktop

```

---

### Post by Brahman on 2006-09-11
Yes, it said this: 

```

ubuntu&ubuntu:~$ 


```

I then typed in sudo apt-get install xubuntu-desktop, hit enter. Notihng. I then typed " $ sudo apt-get install xubuntu-desktop " again nothing.

---

### Post by Najand on 2006-09-11
maybe there is a problem with apt-get. Use aptitude instead of apt-get...
```

$ sudo aptitude install xubuntu-desktop

```

---

### Post by Brahman on 2006-09-11
That still did not work.

---

### Post by Najand on 2006-09-11
hmm, strange... You don't have any errors or something?

---

### Post by Brahman on 2006-09-11
No, after I hit enter it jsut moves down to the next line. And sits there.

---

### Post by Najand on 2006-09-11
You are not typing the "$" sign, too... Do you? If so do it without "$". The reason, we write it is to distingush between working as a normal user or as a root...

---

### Post by Brahman on 2006-09-11
Now it says building packages, and its laoding and other things....is it working?

---

### Post by Najand on 2006-09-11
Hmm, Wait until it finish and see if there is any Errors or Warnings there.

---

### Post by Brahman on 2006-09-11
It says Building tag database....Done. 

Thats all now, and the other things above it say Done to. No error or anything has popped up yet.

---

### Post by Najand on 2006-09-11
So, reboot your system now. You should see the xubuntu splash when rebooting.

---

### Post by Brahman on 2006-09-11
Reboot in hitting the buttin or ctrl+alt+del or does it matter?

---

### Post by Najand on 2006-09-11
try:
```

sudo shutdown -r now

```

---

### Post by Brahman on 2006-09-11
Ok, but now it says its installing like 88 packages and stuff.

---

### Post by Najand on 2006-09-11
Oh, Yeah.... XFCE and its dependencies.

---

### Post by Brahman on 2006-09-11
I went a head and shut it down. Gotta get up eary, but I'm going to try it again tommorrow. Seems thus far it works. Thanks for your help. I'll post more if i run into more problems. Thanks for all your help.

---

### Post by Najand on 2006-09-11
Sure... Ask if you need more help.

---

### Post by Brahman on 2006-09-12
A Err came up with it saying something like Temp. failure arhcive or something. Does it have to connect to the internet?

---

