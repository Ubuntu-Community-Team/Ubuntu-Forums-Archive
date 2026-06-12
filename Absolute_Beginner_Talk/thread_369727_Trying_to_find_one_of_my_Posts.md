---
title: "Trying to find one of my Posts"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-24
I am looking for one of my posts that gave me an excellent page to download a driver for my ATI Radeon 9200SE. It was sometime last week. 
There were only a few steps in terminal to get it to work. I would like to know if there is more than one way in seeing all my posts at once. :confused: 

Sure need some help on this.
Thanks

---

### Post by taurus on 2007-02-24
Maybe this helps.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by kittyhawk63 on 2007-02-24
> **taurus said:**
> Maybe this helps.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

Do I post the "deb" line below into Terminal?

deb [http://www.albertomilone.com/drivers/edgy/latest/32bit](http://www.albertomilone.com/drivers/edgy/latest/32bit) binary/

---

### Post by taurus on 2007-02-24
You need to add that line to the end of your /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by kittyhawk63 on 2007-02-24
> **taurus said:**
> You need to add that line to the end of your /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```

I'm a noobie. Where do I find the  /etc/apt/sources.list ?

---

### Post by taurus on 2007-02-24
Just run that command and it will open it with a text editor.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by kittyhawk63 on 2007-02-24
> **taurus said:**
> Just run that command and it will open it with a text editor.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

Thank you. ):P

---

### Post by nhandler on 2007-02-24
You can also view all your posts by clicking on search, and selecting 'View all your posts' or 'View all your threads'. Or you can click on your name in a thread, and go to 'View all posts by kittyhawk63'

[http://ubuntuforums.org/showthread.php?t=368544](http://ubuntuforums.org/showthread.php?t=368544)

---

### Post by kittyhawk63 on 2007-02-24
> **Cheater said:**
> You can also view all your posts by clicking on search, and selecting 'View all your posts' or 'View all your threads'. Or you can click on your name in a thread, and go to 'View all posts by kittyhawk63'

[http://ubuntuforums.org/showthread.php?t=368544](http://ubuntuforums.org/showthread.php?t=368544)

CHEATER

Thanks for this info. I am new to posting and this will really help. Thanks again. :)

---

### Post by kittyhawk63 on 2007-02-25
> **taurus said:**
> Just run that command and it will open it with a text editor.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

Well, I guess I need simpler instructions. I could not get the instructions given above to work in terminal. I need some simple and clear steps to follow. You know, one, two and three. Or, do this and then this and then this.
In terminal I could not get it to recognize "deb" ,  Any suggestions? I am still trying to get my Radeon 9200SE video card to stop crashing my computer. :confused:

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> Well, I guess I need simpler instructions. I could not get the instructions given above to work in terminal. I need some simple and clear steps to follow. You know, one, two and three. Or, do this and then this and then this.
In terminal I could not get it to recognize "deb" ,  Any suggestions? I am still trying to get my Radeon 9200SE video card to stop crashing my computer. :confused:

Open up your [COLOR="Red"]/etc/apt/sources.list [/COLOR]like they told you above.  Now, you are going to copy/paste the line that begins with "deb...." into your sources.list

Save and exit.  Then:

> sudo apt-get update

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> Open up your /etc/apt/sources.list like they told you above.  Now, you are going to copy/paste the line that begins with "deb...." into your sources.list

Save and exit.  

sudo apt-get update

Hi Maestro23,
I don't know how to open up /etc/apt/sources.list. Is that a line I type in Terminal?

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> Hi Maestro23,
I don't know how to open up /etc/apt/sources.list. Is that a line I type in Terminal?

Yes. Taurus gave you the command in one of his earlier post.

> gksudo gedit /etc/apt/sources.list


---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> Yes. Taurus gave you the command in one of his earlier post.

My problem is that I am getting back a statement that permission is denied. Do I need to type another command to get rid of that?
I know aobut terminal...I just haven't gotten a denied permission before.

---

### Post by taurus on 2007-02-25
Try (from a terminal)

```
sudo nano -Bw /etc/apt/sources.list
```
Exit with <Ctrl>x.  Answer Y for the question and Return.

---

### Post by kittyhawk63 on 2007-02-25
It doesn't work with Ctrl X. It just goes back to my line waiting for another command.

---

### Post by Maestro23 on 2007-02-25
Taurus beat me to it.  Going to suggest nano as well.

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> Taurus beat me to it.  Going to suggest nano as well.

Sorry for the delay. My card caused my computer to crash. What is nano? It put me into another kind of window. What do I do there?

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> Sorry for the delay. My card caused my computer to crash. What is nano? It put me into another kind of window. What do I do there?

nano is a text editor.

Take a look at my 2 screenshots. The first is the command.  The second screen is the sources.list file where you are going to add the "deb" line.  When you add the line, you then :

Ctrl+Oand Ctrl+X.  Then:

> sudo apt-get update

---

### Post by kittyhawk63 on 2007-02-25
Ok. Let me have a few minutes and see if I can get this to work beofe i crash again. I'll get back as soon as possible.

---

### Post by kittyhawk63 on 2007-02-25
Ok. It told me that it wrote 33 lines. What is the next step?

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> Ok. It told me that it wrote 33 lines. What is the next step?

Ctrl+O and Ctrl+X

> sudo apt-get update.

---

### Post by Patrick K on 2007-02-25
What about using the ENVy script. It now supports ATI cards.

---

### Post by Maestro23 on 2007-02-25
> **Patrick K said:**
> What about using the ENVy script. It now supports ATI cards.

I believe he said earlier, he wasn't having luck with the Envy script.  Although if this doesn't work, that will be the next option.

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> Ctrl+O and Ctrl+X

It said it wrote 4 lines. What now? Sorry for the delay. I keep crashing.

---

### Post by kittyhawk63 on 2007-02-25
I tried getting envy. Couldn't figure how to install it. Wish Automatix was working. That is how I got my ATI driver before.

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> It said it wrote 4 lines. What now? Sorry for the delay. I keep crashing.

Are you back at a command prompt in your terminal? If so, do the next step I posted:

> sudo apt-get update

Then proceed to try and install  the program you wanted.

*Didn't we go over some of this last week?  Did you read/bookmark any of those links I gave you to help you with Ubuntu?  I thought your system was up and running.

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> Are you back at a command prompt in your terminal? If so, do the next step I posted:
Then proceed to try and install  the program you wanted.

*Didn't we go over some of this last week?  Did you read/bookmark any of those links I gave you to help you with Ubuntu?  I thought your system was up and running.

Yes, but I had computer problems and had to reinstall Dapper. I also had deleted my subscription list. Did that get rid of all my post as well? I found only the ones I wrote today.

---

### Post by Patrick K on 2007-02-25
You just download it to your desktop and double click it. It will install automatically. Once it is installed, hit alt+ctrl+F1 to go to a console. Then type envy (lower case). It will/should check your hardware and go get the right driver for it. Near the end of its run it will ask if you want it to update the xorg.conf file. I usually (having done this several times) say no and edit xorg.conf myself. The couple times I let it update the file the GUI wouldn't start. It is possible I may be the only person with this issue, though. Since I've not heard anyone else mention this.

---

### Post by kittyhawk63 on 2007-02-25
> **Patrick K said:**
> You just download it to your desktop and double click it. It will install automatically. Once it is installed, hit alt+ctrl+F1 to go to a console. Then type envy (lower case). It will/should check your hardware and go get the right driver for it. Near the end of its run it will ask if you want it to update the xorg.conf file. I usually (having done this several times) say no and edit xorg.conf myself. The couple times I let it update the file the GUI wouldn't start. It is possible I may be the only person with this issue, though. Since I've not heard anyone else mention this.

I found a site to download it. I didn't find anything to download, only a deb statment. I couldn't get "deb" to work in terminal.

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> I found a site to download it. I couldn't get "deb" to work in terminal.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

In terminal:

> sudo dpkg -i ".deb package"

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

In terminal:

Here is what I got from terminal:
kittyhawk63@kittyhawk63:~$ sudo dpkg -i ".deb package"
Password:
dpkg: error processing .deb package (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 .deb package
kittyhawk63@kittyhawk63:~$

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

In terminal:

Thanks for this page. I'll be sure to study it thoroughly.

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> Here is what I got from terminal:
kittyhawk63@kittyhawk63:~$ sudo dpkg -i ".deb package"
Password:
dpkg: error processing .deb package (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 .deb package
kittyhawk63@kittyhawk63:~$

".deb package" was just the example.  The Envy deb pkg that you downloaded goes there.  Just like on the link I gave you.

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> ".deb package" was just the example.  The Envy deb pkg that you downloaded goes there.  Just like on the link I gave you.

I haven't downloaded the envy deb pkg. I found a site with it, but couldn't get the deb line for terminal to work.

---

### Post by kittyhawk63 on 2007-02-25
Maestro23
Why doesn't my terminal recognize deb pkgs? Is that where I put deb pkgs to install?

---

### Post by Patrick K on 2007-02-25
For the Envy script go here: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Download "envy_0.8.2-0ubuntu1_all.deb" by right clicking on it and selecting "save link as". Save it to your desktop. This will start the download. Once it is downloaded double click and it will start the install process. Then run it as i posted above.

---

### Post by kittyhawk63 on 2007-02-25
> **Patrick K said:**
> For the Envy script go here: 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Download "envy_0.8.2-0ubuntu1_all.deb" by right clicking on it and selecting "save link as". Save it to your desktop. This will start the download. Once it is downloaded double click and it will start the install process. Then run it as i posted above.

Thanks. I guess Maestro gave up on me. Iv'be been reading the link on how to install deb pkgs that he gave me. I thank him also for the link.

---

### Post by kittyhawk63 on 2007-02-25
Do I use the word "deb" in from of a deb pkg when placing the line in terminal?

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> Thanks. I guess Maestro gave up on me. Iv'be been reading the link on how to install deb pkgs that he gave me. I thank him also for the link.

Sorry, just got done installing Office 2.1.  Follow Patrick's way if it seems easier for you.

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> Sorry, just got done installing Office 2.1.  Follow Patrick's way if it seems easier for you.

I havn't finished reading on installing programs. Do I add the word "deb" when pasting a deb line into terminal. If I don't that me be why it doesn't recognize the file or folder as it keeps telling me.

---

### Post by kittyhawk63 on 2007-02-25
Maestro23,
When I see two lines that need to be place into terminal like:

sudo aptitude update
sudo aptitude install build-essential

do I copy both lines and paste as a unit or copy and paste each line sepratately and hit enter after each line?

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> I havn't finished reading on installing programs. Do I add the word "deb" when pasting a deb line into terminal. If I don't that me be why it doesn't recognize the file or folder as it keeps telling me.

No. Example:

> cd Desktop
sudo dpkg -i opera_9.10-20061214.6-shared-qt_en_i386.deb

*[COLOR="Red"]opera_9.10-20061214.6-shared-qt_en_i386.deb[/COLOR] was downloaded to the user's Desktop.  So he changed (cd) to his Desktop directory.

*Then ran his [COLOR="Red"]dpkg -i [/COLOR]command on [COLOR="Red"]opera_9.10-20061214.6-shared-qt_en_i386.deb[/COLOR]

So, get to where ever you downloaded your file and do the same thing.

---

### Post by kittyhawk63 on 2007-02-25
Let's see if I got this. If I get a line with the word deb in front of it, I copy the line starting after the word deb. Is that correct?

---

### Post by kittyhawk63 on 2007-02-25
I just reread your last post and I think I got it.

I have just come back after my seventh crash while reading and making replies to this post.
Grrrrr!

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> Let's see if I got this. If I get a line with the word deb in front of it, I copy the line starting after the word deb. Is that correct?

You are mixing stuff up here.  Are you still talking about the line that was added to your etc/apt/sources.list ?  I thought you were good to go on that.  Patrick and I have been trying to walk you thru installing the Evny .deb pkg.  Which one are you trying to do now?

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> You are mixing stuff up here.  Are you still talking about the line that was added to your etc/apt/sources.list ?  I thought you were good to go on that.  Patrick and I have been trying to walk you thru installing the Evny .deb pkg.  Which one are you trying to do now?

I'm with you, but I could be confused. I'm not talking about nano. Don't deb pks also go into terminal using the sudo command?

---

### Post by kittyhawk63 on 2007-02-25
Where were we with Envy? I can't find it yet in my programs.

---

### Post by Maestro23 on 2007-02-25
> **kittyhawk63 said:**
> I'm with you, but I could be confused. I'm not talking about nano. Don't deb pks also go into terminal using the sudo command?

Yes.  If you have the Envy deb pkg downloaded, follow the example I posted above.

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> Yes.  If you have the Envy deb pkg downloaded, follow the example I posted above.

Ok. I'm going to let you go, I know that you have spent a lot of time with me. I am going to try and download and install Envy. I haven't downloaded Envy yet for installation. I will carefully follow your instructions. Thanks again Maestro23.

---

### Post by Patrick K on 2007-02-25
Have you downloaded Envy, yet?

Envy runs from the terminal (Applications>Accessories). You may need to type:> sudo envy to run it. If you use sudo, you will need to enter your password. 

The way I'm giving you to get Envy is not through any of the package installers. This way is more like downloading and installing a windows program. For some things, it's just easier this way.

---

### Post by kittyhawk63 on 2007-02-25
> **Patrick K said:**
> Have you downloaded Envy, yet?

Envy runs from the terminal (Applications>Accessories). You may need to type: to run it. If you use sudo, you will need to enter your password. 

The way I'm giving you to get Envy is not through any of the package installers. This way is more like downloading and installing a windows program. For some things, it's just easier this way.

I've not install envy yet. I tried and checked with your sudo command. Here is the reply:

kittyhawk63@kittyhawk63:~$ sudo envy
Password:
sudo: envy: command not found
kittyhawk63@kittyhawk63:~$
 On my way to install Envy right now. Looking for it on the Internet.

---

### Post by Maestro23 on 2007-02-25
Envy: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by Patrick K on 2007-02-25
It's at the address I posted above. No need to hunt for it.

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> Envy: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

THANKS

---

### Post by kittyhawk63 on 2007-02-25
Installing Envy right now. Thanks to both of you.

---

### Post by Patrick K on 2007-02-25
Here it is again:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
This is the fellow who wrote its web site.

Here is the file:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb)

---

### Post by kittyhawk63 on 2007-02-25
Thanks to both of you. My video driver is now installed via Envy. I am now going to open up my text editor and copy and paste the instructions that I received from both of you and print it out. I can't thank either of you enough for sticking with me through this.
It is 11:27 pm my time. Good night to you both.
kittyhawk63

---

### Post by Patrick K on 2007-02-25
Glad to be of help.

---

### Post by Maestro23 on 2007-02-25
> **Patrick K said:**
> Glad to be of help.

Ditto.  Please mark this 6 page thread RESOLVED.:)

---

### Post by shareMenaPeace on 2007-02-25
Hi, 
the file extension "deb" means it is a "debian linux" file. Made from source code - compiled as a deb, a debian package (pkg).

As ubuntu is based on debian those packages if avaiable can be downloaded and then executed with double click on it.

Great you got it going sleep well :)

Cheers

---

### Post by kittyhawk63 on 2007-02-25
> **Maestro23 said:**
> Ditto.  Please mark this 6 page thread RESOLVED.:)

Thanks gain Maestro. I "will" mark it resolved.

---

