---
title: "Getting an Accelerated Desktop"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by carowyn on 2008-03-04
So, first of all, I'm sorry if this has already been answered, but I couldn't find any help either on this forum or others... maybe I am not searching correctly...?

Anyway, I really want to get the kubuntu-desktop metapackage (I think that's what I read somewhere that it is called...?) so that my desktop doesn't look like a Mac from the 90s :P  but what I read online to do was go to the Synaptic Package Manager and "get kubuntu-desktop"... Well, I'm not entirely sure what that means.  I did a search and it found nothing.  I was connected to the internet.  Do I need to go online and download it and then use the Synaptic Package Manager?  Can someone please help me? :(

--the absolutest beginner

---

### Post by tszanon on 2008-03-04
You have 2 options to get there:
1. use synaptic package manager (System > Administration > Synaptic) to install it. In synaptic, search for "kubuntu-desktop" and install it. It'll download all necessary files and then install it.
2. you could download the cd image for kubuntu and reinstall the system. By default, the user interface will be KDE instead of Gnome.

---

### Post by FreewareFan on 2008-03-04
Hi.  It's really easy.  Just go to System - Administration - Synaptics Package Manager and click on it.   The program will ask you for your password, and then start.

Once it starts, just click on the search button, and enter the name of the program you want, in this case, kubuntu-desktop.   Click OK, and it will search for the program.   When the results show up, you find the one you want, and right-click on it, and choose Mark For Installation.    Once you've done that, just clidk on the green check mark up on top of the program, and it will install your selected program for you.  

That's about it.    Hope this helps you out!

FwF

---

### Post by carowyn on 2008-03-04
When I do the search, on the left hand side there is a box that says "All" and then "kubuntu-desktop" (what I searched for) but then if I try to click on that, nothing happens.  In the main part of the window (like where it says "package", "installed version", "latest version", "description" along the top) there is nothing at all....

---

### Post by carowyn on 2008-03-04
well, i guess i will download the cd image for kubuntu and just reinstall the os from that one... i'm sad that i can't figure it out though.  i'm sure i'll need to use synaptic again in the near future...

---

### Post by FrozenFox on 2008-03-04
You don't see kubuntu-desktop like in this screenshot after you search for it?

After you search, it should bring that up. To install it, all youd need to do is click the check box (mine is green, which means INSTALLED. Yours would be an empty checkbox. Youd just select Mark For Installation then click Apply at the top. Any software you can think of can be installed the same way.

---

### Post by carowyn on 2008-03-04
Nope, I don't see that... There is nothing there at all to click.  That's why I am so confused.  I don't know why it isn't there though.  Like I said before, I am connected to the internet.  I clicked 'search' and typed in 'kubuntu-desktop'... but then nothing is found :(

---

### Post by FrozenFox on 2008-03-04
EDIT: Wow, dyslexic with left and right, lol. fixed. 

Oh, did you click reload in the upper left before you searched? I would suggest checking to make sure you have all the repositories enabled (under system or preferences, it's called "Software Sources") but I'm 85% sure kubuntu-desktop does not use anything that would not be in the default repositories.

---

### Post by carowyn on 2008-03-04
file:///home/carowyn/Desktop/Screenshot.png


This is what mine looks like... :S

---

### Post by carowyn on 2008-03-04
oh wait... i dont know how to post images hehe

---

### Post by FrozenFox on 2008-03-04
Post a reply, scroll down a little to 'advanced options', manage attachments, and attach the file

---

### Post by carowyn on 2008-03-04
there we go :)

---

### Post by kwacka on 2008-03-04
If you open a terminal and type:

sudo apt-get install kubuntu-desktop

all packages required should be installed. If you get any not found error messages, check that you have repositories enabled.

Finally, log out. At the login screen click on options in the bottom corner - is there a KDE/Kubuntu option?

---

### Post by FrozenFox on 2008-03-04
Indeed. If you can't get that to show up, follow my previous directions to find the software sources deal, and enable all repositories from there.

However, on further reading your comment, I don't understand why you're switching from gnome to kde (kubuntu). Gnome doesn't have to look how it does by default. It doesn't even have to have 2 bars either, you can totally customize your setup. If that's your problem, you won't be more impressed with KDE, because default kde doesnt look that great either.

Take a look at gnome-look.org and check out the GTK2 themes.. any of them can skin ubuntu.

[http://gnome-look.org/CONTENT/content-pre1/74813-1.jpg](http://gnome-look.org/CONTENT/content-pre1/74813-1.jpg)  for instance, here's a radically different skin setup..
[http://gnome-look.org/CONTENT/content-pre1/44080-1.jpg](http://gnome-look.org/CONTENT/content-pre1/44080-1.jpg)      another one..


kde-look.org of course is for kde stuff.

Gnome can actually look very good if you want it to, sometimes even better than kde. (Though im a kde guy myself).

---

### Post by carowyn on 2008-03-04
Yay!  Thanks, Kwacka!  I guess I had no repositories (??).  I don't know, but I clicked them all and then it worked... hehe

Thanks, you guys, for all your awesome help :D

---

### Post by FrozenFox on 2008-03-04
Sweet. Please go to thread tools at the top of this page and mark the thread as solved if you have everything resolved ;)

---

