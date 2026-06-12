---
title: "ony get a failsafe terminal! Can I start over fresh? It worked fine"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by gumpontheweb on 2008-01-29
I see a few people with the same problems I had but now my problems are Horrible!
First let me tell you that I have used computers my whole life but not ubuntu. I am just now learning, or trying to learn the terminal commands. After reading for a while I think I am ready to even be helped!
I can't even say all the crazy stuff that has been attempted in trying to fix it. Anything that I have tried has not fixed it permanently. Now, after my brother tried using the synaptic graphical update manager, the thing broke?! when I try to log on I get an error message. Besides actually using a camera to take a picture I have to just type out what the error says? If I try to normally log in I just get an arrow with nothing else.
When I try to change the session to failsafe teminal and log in I see this:
This is failsafe xterm session. You will be logged into a terminal console so that you may fix your system If yo cannot log in any other way. To exit the terminal emulator, type 'exit' and an enter into the window

What are my options?
I also want to mention that the source list isn't correct(i think)
I dont get anything from anywhere except "debian"
Hopefully this thread will help others besides myself...

---

### Post by asmoore82 on 2008-01-29
:confused: need more information than that

---

### Post by JoshuaRL on 2008-01-29
Yeah, just type what the error says.  Man, don't let brothers play around with Synaptic.  They're the worst.  :P

---

### Post by gumpontheweb on 2008-01-29
god you guys are quicker than I can type!!!!

---

### Post by JoshuaRL on 2008-01-29
> **gumpontheweb said:**
> god you guys are quicker than I can type!!!!

Heehee.  Just try getting that anywhere else.  That's why this is my favorite distro.

---

### Post by gumpontheweb on 2008-01-29
I hadn't finished typing!!! please help  me...
I was worried after a minute:lolflag::lolflag:

---

### Post by JoshuaRL on 2008-01-29
Cool, just post what the error is.  That will give us an idea of what the issue is.

Although you could always try:

```

gksu synaptic

```

and search around for broken dependencies through the filter.  It may bring something up.

---

### Post by gumpontheweb on 2008-01-29
I have no cd drive/player. 
The only thing is that I would like to keep the movies and stuff like my music which is all in one file folder that was on the desktop. I thought that might not be incredibly hard! I hope not!!!

---

### Post by gumpontheweb on 2008-01-29
> **JoshuaRL said:**
> Cool, just post what the error is.  That will give us an idea of what the issue is.

Although you could always try:

```

gksu synaptic

```

and search around for broken dependencies through the filter.  It may bring something up.
I can get synaptic to run but I think the source list is wrong. It is only "http:debian" (not exactly) Where do I even start?

---

### Post by gumpontheweb on 2008-01-29
synaptic doesn't reload correctly. I get:
Could not download all repository indexes

---

### Post by JoshuaRL on 2008-01-29
Well, I'll tell you a story.

I have an Inspiron 5100 with a graphics card that's a bear to get running right.  I did four (that's right, FOUR) reinstalls before I got it working.  But since, I've learned that there are tools to fix almost anything software-related without reinstalling.

So I would suggest you try to see if you can just fix it, you'll learn a lot in the process too.  It may not be as easy, but it's the better choice all around.

---

### Post by jaytek13 on 2008-01-29
So, is that your main problem? You can log into the graphical interface fine but your synaptic sources are messed up? 

If so, you can do a 

```

gksudo gedit /etc/apt/sources.list

```

and check what's in that file.

---

### Post by gumpontheweb on 2008-01-29
I don't know what [source] means.
when I try to put in the line you gave me nothing happens at all?
the window is 1/4 the scrreen in the bottom right. just an emulator buut I can get synaptic to run by:
sudo synaptic

---

### Post by JoshuaRL on 2008-01-29
[http://ubuntuforums.org/showthread.php?t=681068&highlight=sources.list](http://ubuntuforums.org/showthread.php?t=681068&highlight=sources.list)

The post at the bottom has a sources.list, but he has almost everything commented out.  So take the #s out from in front of all the lines that start with "deb".

But I'm telling you, this will be easier if you could post the error.

---

### Post by gumpontheweb on 2008-01-29
> **JoshuaRL said:**
> [http://ubuntuforums.org/showthread.php?t=681068&highlight=sources.list](http://ubuntuforums.org/showthread.php?t=681068&highlight=sources.list)

The post at the bottom has a sources.list, but he has almost everything commented out.  So take the #s out from in front of all the lines that start with "deb".

But I'm telling you, this will be easier if you could post the error.
which error?
I dont know how to get to that file?

---

### Post by gumpontheweb on 2008-01-29
> **JoshuaRL said:**
> Well, I'll tell you a story.

I have an Inspiron 5100 with a graphics card that's a bear to get running right.  I did four (that's right, FOUR) reinstalls before I got it working.  But since, I've learned that there are tools to fix almost anything software-related without reinstalling.

So I would suggest you try to see if you can just fix it, you'll learn a lot in the process too.  It may not be as easy, but it's the better choice all around.
I agree with you completely! But I think all my software is broken. 
I can't get to anything at all!

---

### Post by jaytek13 on 2008-01-29
> **gumpontheweb said:**
> which error?
I dont know how to get to that file?

[source] was a typo


You type 

```

gksudo gedit /etc/apt/sources.list

```

into the terminal and it will open up your sources file. The person who posted after me posted a link to the default file. If your sources.list file looks differently you could probably just copy/paste and uncomment some things and it should solve the problem.

---

### Post by gumpontheweb on 2008-01-30
Nothing happens at all!

---

### Post by gumpontheweb on 2008-01-30
I don't think gnome or anything is working!
I see an error that reads:
could not load support for 'gnome': libgnome.so: cannot open shgared object file!
I didn't tell you that I have the broken laptop(that was working perfectly) on my lap while typing on the desktop to post to you!

---

### Post by JoshuaRL on 2008-01-30
Do:

```

nano /etc/apt/sources.list

```

See what's in there.

But please, post the error you get at startup.  Please.  I'm guessing it has something to do with Xorg?

---

### Post by gumpontheweb on 2008-01-30
> **JoshuaRL said:**
> Do:

```

nano /etc/apt/sources.list

```

See what's in there.

But please, post the error you get at startup.  Please.  I'm guessing it has something to do with Xorg?
It's empty! I see nothing except [NewFile] at the bottom
It says:GNU Nano 2.0.6         File: /ect/apt/sources.list



         [NEW FILE]

---

### Post by JoshuaRL on 2008-01-30
Okay, that would be a problem.  I'm not sure how to fix that, other than just creating a new one.

Now, what is the error that comes up when you start?

---

### Post by gumpontheweb on 2008-01-30
I think I am gonna have to do something BIG.....

---

### Post by gumpontheweb on 2008-01-30
> **JoshuaRL said:**
> Okay, that would be a problem.  I'm not sure how to fix that, other than just creating a new one.

Now, what is the error that comes up when you start?
This is failsafe xterm session. You will be logged into a terminal console so that you may fix your system If yo cannot log in any other way. To exit the terminal emulator, type 'exit' and an enter into the window
SEE I told you it was BAD!!!

---

### Post by JoshuaRL on 2008-01-30
What happens when you try:

```

startx

```

---

### Post by gumpontheweb on 2008-01-30
I found a sources file and directory but I cant change it or anything else?
Is there any way to get the main opertating files without re-installation.
I can't even re-install since I have no cd drive at the moment!!!
What are my options???

---

### Post by gumpontheweb on 2008-01-30
xauth: creating new autority file /home/chris/.serverauth.5372

X: user not authorized to run the x server, aborting.
couldn't get a file descriptop referring to the console
@thelaptop:~$

---

### Post by gumpontheweb on 2008-01-30
> **JoshuaRL said:**
> What happens when you try:

```

startx

```

xauth: creating new autority file /home/chris/.serverauth.5372

X: user not authorized to run the x server, aborting.
couldn't get a file descriptop referring to the console
@thelaptop:~$

---

### Post by JoshuaRL on 2008-01-30
Yeah, just do:

```

login

```

that will let you login to your superuser account.  Then use sudo to do any admin tasks and you should be able to view and edit all the .conf files.

---

### Post by gumpontheweb on 2008-01-30
> **JoshuaRL said:**
> Yeah, just do:

```

login

```

that will let you login to your superuser account.  Then use sudo to do any admin tasks and you should be able to view and edit all the .conf files.
login gives me:
no utmp entry. you must exec "login" from the lowest level "sh"

I did:
 sudo startx
and got:
xauth: creating new autority file /home/chris/.serverauth.5372

Fatal server error:
Server is already active for display 0
if this sewrver is no longer running, remove /tmp/.xo-lock and start again

SOOO much typing!

---

### Post by jaytek13 on 2008-01-30
> **gumpontheweb said:**
> login gives me:
no utmp entry. you must exec "login" from the lowest level "sh"

I did:
 sudo startx
and got:
xauth: creating new autority file /home/chris/.serverauth.5372

Fatal server error:
Server is already active for display 0
if this sewrver is no longer running, remove /tmp/.xo-lock and start again

SOOO much typing!


Just to throw this out there, was your ubuntu installation working fine and then it broke? If so, what were you doing right before all this trouble started?

---

### Post by gumpontheweb on 2008-01-30
> **jaytek13 said:**
> Just to throw this out there, was your ubuntu installation working fine and then it broke? If so, what were you doing right before all this trouble started?
first, when I tried to get rid of adept manager with synaptic package manager everything went screwy, The desktop went black. when i open my home folder i would  get this pop-up saying:
Could not open location 'file:///home/user'
There is no default action associated with this location
Then from there it was a bunch of adding and removing stuff from synaptic.
synaptic is what I was doing so I tried to redo what was in history and it got worse!
so I figured out dselect and got synaptic and the internet to work again but my bro ran update manager and now I cant even login

---

### Post by gumpontheweb on 2008-01-30
Now I dont have anything right!
Like I asked, is there a way to start over fresh over the internet without losing your stuff. I guess I mean without re-installing and losing my music& movies which is all in 1 file

---

### Post by jaytek13 on 2008-01-30
> **gumpontheweb said:**
> first, when I tried to get rid of adept manager with synaptic package manager everything went screwy, The desktop went black. when i open my home folder i would  get this pop-up saying:
Could not open location 'file:///home/user'
There is no default action associated with this location
Then from there it was a bunch of adding and removing stuff from synaptic.
synaptic is what I was doing so I tried to redo what was in history and it got worse!
so I figured out dselect and got synaptic and the internet to work again but my bro ran update manager and now I cant even login

So, were you on KDE when you removed adept? Just from trying to remove adept I can see by doing so it will also automatically uninstall kubuntu-desktop, which you need for, well, the GUI. 

What desktop are you on now? You say you can open synaptic but what desktop are you using to do so?

---

### Post by gumpontheweb on 2008-01-30
> **jaytek13 said:**
> So, were you on KDE when you removed adept? Just from trying to remove adept I can see by doing so it will also automatically uninstall kubuntu-desktop, which you need for, well, the GUI. 

What desktop are you on now? You say you can open synaptic but what desktop are you using to do so?
NO DESKTOP that is the problem that started this!!
now there are more problems! I still had a working system after removing adept but I never got my desktop back.
when I try to login I get the error:
This is failsafe xterm session. You will be logged into a terminal console so that you may fix your system If yo cannot log in any other way. To exit the terminal emulator, type 'exit' and an enter into the window
then I get a quarter screen window in the bottom right with a promt to type in

---

### Post by jaytek13 on 2008-01-30
Okay, so you don't have a desktop, but you do have access to the command line, right? 

I think the first step would be getting your desktop back. Your previous error said x was already running... but apparently it has nothing to display.

so

sudo apt-get install kubuntu-desktop

or

sudo apt-get install ubuntu-desktop

Depending on whether you want to use KDE (kubuntu) or Gnome (ubuntu).

---

### Post by gumpontheweb on 2008-01-30
> **jaytek13 said:**
> Okay, so you don't have a desktop, but you do have access to the command line, right? 

I think the first step would be getting your desktop back. Your previous error said x was already running... but apparently it has nothing to display.

so

sudo apt-get install kubuntu-desktop

or

sudo apt-get install ubuntu-desktop

Depending on whether you want to use KDE (kubuntu) or Gnome (ubuntu).
I get Package ubuntu-desktop is not available,but it is reffered to by anotherpackage. this may mean that the package is missing,has been....

I think my source list is BAD
I dont really know but i think it was gnome? I don't care!
I think it's a terminal emulator, not the terminal, BUT i don't know

---

### Post by jaytek13 on 2008-01-30
> **gumpontheweb said:**
> I get Package ubuntu-desktop is not available,but it is reffered to by anotherpackage. this may mean that the package is missing,has been....

I think my source list is BAD


Okay so we'll start with that. Apparently there is no sources.list file in /etc/apt/sources.list. The removal of this file probably occured when you removed adept. So, you will have to create a new one.

sudo nano /etc/apt/sources.list


then it would seem you will have to manually copy the sources file linked earlier into that file. After doing so, save it, then try sudo apt-get install (k)ubuntu-desktop again.

And you were probably using kubuntu-desktop. Adept is the default package manager for kubuntu, while synaptic is the default pkg manager for ubuntu(gnome).

---

### Post by gumpontheweb on 2008-01-30
> **jaytek13 said:**
> Okay so we'll start with that. Apparently there is no sources.list file in /etc/apt/sources.list. The removal of this file probably occured when you removed adept. So, you will have to create a new one.

sudo nano /etc/apt/sources.list


then it would seem you will have to manually copy the sources file linked earlier into that file. After doing so, save it, then try sudo apt-get install (k)ubuntu-desktop again.

And you were probably using kubuntu-desktop. Adept is the default package manager for kubuntu, while synaptic is the default pkg manager for ubuntu(gnome).
will I have to copy all or just withou# in the begining of the line

---

### Post by jaytek13 on 2008-01-30
> **gumpontheweb said:**
> will I have to copy all or just withou# in the begining of the line


Well, you don't have to copy the # comments that are actually comments, but everything that starts with deb. This isn't totally necessary but I'm not sure which source contains the files for the desktops.

---

### Post by gumpontheweb on 2008-01-30
I made the file just like it is and dont get anything different???
I am not getting to the internet it seems?
what now???

---

### Post by gumpontheweb on 2008-01-30
when I try to install kubuntu i get an error a little different!
reading package list...done 
building dependency tree
reading state information...Done
E:couldn't find package kubuntu-desktop


Does the"E" mean it is looking in "E" and not the internet?

---

### Post by jaytek13 on 2008-01-30
> **gumpontheweb said:**
> when I try to install kubuntu i get an error a little different!
reading package list...done 
building dependency tree
reading state information...Done
E:couldn't find package kubuntu-desktop


Does the"E" mean it is looking in "E" and not the internet?


I don't believe that is what the E means. 

I'm sure there is another easier way to check if you're connected to the internet, but this is what I know.

At the prompt, type lynx. It will bring up a text based web browser. Try to navigate to a web page with it.

---

### Post by gumpontheweb on 2008-02-01
I had to sleep last time....  that's why I left so abruptly...
I want to thank jaytek 13!!! Sorry for passing out on you

---

### Post by gumpontheweb on 2008-02-01
When I try to run lynx, I get an error message...
I dont have internet connection???
I think if I could get the internet wairelessly working , I could figure the rest out MUCH EASIER!!!
My desktop computer is shared so I can't use it all the time.
How can I get internet working ,Then wirelessly?

---

### Post by gumpontheweb on 2008-02-01
I got the ubuntu-desktop package which fixed lots of problems except my wirless internet?
It will find names of wireless places,but not connect to the internet?
I also don't have the same icon for my network manager. Could I have had kubuntu?
How can I get the wirless network manager I .
Or even get any wireless to work?
I know it is do-able since I had it working easy from the install

---

