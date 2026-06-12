---
title: "Cannot get Celtx to work"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Nodestar on 2008-04-13
I've tried every way possible to get Celtx to work. For the past two days I've installed it over and over again both in Terminal and with the GUI. In usr/local in /opt in home directory. I've downloaded to desktop. Extracted to usr/local/celtx/celtx to home/justin/.celtx/celtx. I've also installed to /opt then used terminal commands to put a file in /bin so I could just use celtx to run the program and not the full path file. This didn't seem to work. I could not find any files related to celtx in the /bin ( I didn't fully understand the mechanics behind this one. I just followed someones advice in one of the many post on this subject I've read.) 

Everything you can imagine I've tried. I can only get it to work one way. By installing to one of the various dir. and using the Sudo command in the terminal. Followed by it's path.
Example Sudo /usr/local/celtx/celtx 

Launchers will not work because the execution files don't seem to work. Every guide or tutorial says that the file simply titled celtx within the celtx folder is the one that executes the program. This does not work for me. You should be able to double click this file and then select Run. When I do this nothing happens. You can also choose run in terminal. When I select this option a window will pop up for less than a second and disappear. And then nothing else happens.

I've already been through 3 post regarding this subject. Some suggestions have hinted towards a problem with my administration privileges. Whenever I install Celtx it normally locks me out of doing anything with it's files because the files are owned by root. I've used the gksudo nautilus terminal command to give full privileges to me. Giving myself the power to read write and execute all of celtx files. This has not helped. Also I am the only person using this machine and the only user Ubuntu has. Also my password works when prompted by the Terminal for various things. 

I'm just trying to get the program to run from a launcher or more specifically from the Application Menu. 

Thank You for listening.


Edit: I've made 3 post myself and searched through many more. For most people the above methods just simply work. I've found only one other person who seems to be having this same problem. 
His post is here [http://ubuntuforums.org/showthread.php?t=576125&highlight=celtx](http://ubuntuforums.org/showthread.php?t=576125&highlight=celtx)
He is the Original Poster

---

### Post by AvixK7 on 2008-04-14
I fixed my problem by tracing it to a missinhttp://www.google.ca/ig?hl=eng (newer) library file that celtx required. Not sure if this is the same problem for you. I posted a thread on the celtx forum with the same question and updated it with the fix I used. Search my my user name and you'll find it. avixk7 :)

EDIT:

Here you go, hope it helps :) I have my doubts that your problem has to do with administrative privileges.

[http://forums.celtx.com/viewtopic.php?t=5501&highlight=](http://forums.celtx.com/viewtopic.php?t=5501&highlight=)

---

### Post by Nodestar on 2008-04-14
Yea I went through that in the begining. It's been a couple days now but I think I followed a wiki guide on how to get it. Typed a command in in the Terminal. It failed and said I needed yum to download libstdc++5. I downloaded yum from the terminal and then downloaded libstdc++5. I don't get the error associated with missing libstdc++5 anymore. 

But it still doesn't work.

In the post you made on Celtx forums there is a guy posting, Screen Name: XerXeX. I'm having the same problems as him. I can only run it in the terminal with the sudo command. The Launchers won't work. Even trying to run it from the shell script directly won't work.

---

### Post by Tatty on 2008-04-14
Have you tried following the installation instructions from the official wiki?

Try following them and post back if you get stuck at any specific stage.

[http://wiki.celtx.com/index.php?title=Installation#For_Linux]("http://wiki.celtx.com/index.php?title=Installation#For_Linux")

---

### Post by Nodestar on 2008-04-14
Yes that is the Wiki I installed from. However after rereading it I'm going to look into two things.

First: 32-bit librarys 

> If you're running a 64-bit build, ensure the 32-bit libraries are installed. Just search for the string "ia32" within synaptic. You might have to install the normal "ia32-libs" and also "ia32-libs-gtk", perhaps more.

I'm going to try and install those. I'm running Ubuntu 7.10 and before that I was running Windows XP. Not sure whether I'm 32-bit or 64-bit but I'm assuming I'm 64-bit.

Second:

Further down that Wiki page you'll see a title "Launching for the Tirst Time"

> To launch Celtx double click the movie clapper icon like the one below.

The application will open and display the Splash Page.

The Icon is title
Celtx_clapper_icon.png

I have never seen this file before.

---

### Post by Nodestar on 2008-04-14
When I search ia32-libs-gtk in the Synaptic I get nothing.
When I search ia32-libs I get nothing. 
When I search ia32 I get the following:

Elio - Boot Loader for systems useing EFI-based firmware

GNU-EFI - Library for developing EFI Applications

Microde.ctl - Intel Microde Utility

refit - Graphic bootloader for EFI-based ia32 systems


Which ones do I need?

---

### Post by Tatty on 2008-04-14
search for "ia32" in synaptic.  it has popped up with the packages on my machine.

to see if you are running 32bit or 64bit ubuntu use this:
```
uname -m
```

x86_64 would mean you have 64bit ubuntu installed.

---

### Post by Nodestar on 2008-04-14
When I type uname -m in the Terminal I get i686

Also I searched for ia32 and I listed the packages avliable for download in my post above. Which ones do I need though? None of their descriptions make sense.

---

### Post by Tatty on 2008-04-14
You have a 32bit OS currently so you do not need those ia32 libraries

Jets just check the steps to install this:

If you are using it for only one user on one machine then simply extract the downloaded tar file to your home folder.  You can then run the application from there according to the wiki.

If you want multiple users to be able to use it then do this:

1. copy the file to /usr/local

2. open a terminal and cd to /usr/local : cd /usr/local

3. untar the file: sudo tar zxf /path/to/Celtx.tar.gz

4. run: sudo /usr/local/celtx/celtx

According to the wiki, now you can run the software as any user with: /usr/local/celtx/celtx

Post back if you have any problems.

---

### Post by Nodestar on 2008-04-14
Yea I've done all that before. I've tried it all. I've done home/justin/.celtx/celtx
/usr/local/celtx/celtx and I've tried installing in /opt and then in bin.
I've tried everything in my original post. Installing it should not be the problem anymore. Just making it run.
I'm pretty much out of ideas at this point though. 

I went through my old post that led to this one [http://ubuntuforums.org/showthread.php?t=753780&page=3](http://ubuntuforums.org/showthread.php?t=753780&page=3)

Just can't figure out why the Launchers arn't working. Still thinking it has do to with permissions and the root owning the files.

---

### Post by Tatty on 2008-04-14
Ok I have re-read your origional post closer, sorry I missed a few points you made in it.

Firsly, do you get any error messages when trying to run the software?

Secondly, i am wondering if you changing the ownership of the file might be upsetting it somehow.

Getting it to run from a launcher will be a simple case of right clicking on the menu and choosing "edit menus" then adding an entry for it.

Also, since you are the only person using this softare, have you tried installing it to your /home?

---

### Post by Nodestar on 2008-04-14
Ok it's finally over. I looked over the Wiki again and rembered the part where it says you need to delete the .celtx files and .greyfirst files. I have done this before but I guess not when everything else was fixed. Thank goodness it's finally over. 

Thank you for all your help everyone.

---

### Post by Tatty on 2008-04-14
Oh good!  :) well done

---

### Post by UbiOneCanubi on 2008-04-27
> **Nodestar said:**
> Ok it's finally over. I looked over the Wiki again and rembered the part where it says **you need to delete the .celtx files and .greyfirst files.** I have done this before but I guess not when everything else was fixed. Thank goodness it's finally over. 

Thank you for all your help everyone.

Hello. I was wondering how you deleted your .greyfirst and .celtx directory files in the most descriptive way you can describe this to me.

I'm brand spanking new to Ubuntu and any sort of technical computer stuff. Glad to be a part of this community even if I don't know what I'm doing :D

Apart from needing to know how to do that I'm happy blundering around like I have so far.

Thanks,

Ubi

---

### Post by halfhaggis on 2008-05-01
Hey UbiOneCanubi

Open a terminal (Applications->Accessories->Terminal)

Type at the prompt:
```
rm -r .celtx .greyfirst
```

That should do it.

To navigate to the files via nautilus (the graphical file manager), open your home folder (Places->Home) and hit Ctrl-H. This will display the hidden folders and files (i.e. those preceded with a '.') You should be able to delete it from there.

If the directories cannot be deleted, then you probably don't have permission to remove them (if, for example, you created them as the root (or super) user.

To check, run:
```
ls -al ~|grep celtx; ls -al|grep greyfirst
```

If it says root next to the file names, then you'll have to run 
```
sudo rm -r .celtx .greyfirst
```

to get rid of those directories.

If you have problems, please post the out put of 
```
ls -al ~|grep celtx; ls -al|grep greyfirst
```

---

### Post by UbiOneCanubi on 2008-05-02
Hey halfhaggis!

Thank you for the reply! I just got back from Malaysia so I'll give everything a go and let you know how I fare.

Thanks again :)

Ubi

---

### Post by UbiOneCanubi on 2008-05-02
Alright, still not working for me.

I ran [COLOR="Blue"]rm -r .celtx .greyfirst[/COLOR] to which the response came back.
> sam@UbiOneCanubi:~$ rm -r .celtx .greyfirst
rm: cannot remove `.celtx': No such file or directory
rm: cannot remove `.greyfirst': No such file or directory
sam@UbiOneCanubi:~$ 


From there I ran [COLOR="Blue"]ls -al ~|grep celtx; ls -al|grep greyfirst[/COLOR] and there was no result. I.e.
> sam@UbiOneCanubi:~$ ls -al ~|grep celtx; ls -al|grep greyfirst
sam@UbiOneCanubi:~$ 

From that I followed the installation instructions found on the Celtx wiki page and the results were this.
> sam@UbiOneCanubi:~$ cd /usr/local
sam@UbiOneCanubi:/usr/local$ sudo tar zxf /home/sam/Desktop/to/Celtx.tar.gz
[sudo] password for sam: 
tar: /home/sam/Desktop/to/Celtx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
sam@UbiOneCanubi:/usr/local$ 


Yeah, I don't really know what to do from here.

> sam@UbiOneCanubi:/$ cd /home/sam/Desktop
sam@UbiOneCanubi:~/Desktop$ ls
[COLOR="Red"]Celtx.tar.gz[/COLOR]
sam@UbiOneCanubi:~/Desktop$ 

I checked that out and don't know if the fact that the Celtx.tar.gz is the colour red has anything to do with anything.

Any help would be greatly appreciated.

Ubi

---

### Post by halfhaggis on 2008-05-03
Ubi:

I see your problem. Thanks for posting the terminal output:

You haven't installed this before, so there is no need to remove the .celtx and .greyfirst directories. This is the reason why, when you try to remove them with the 'rm' command, it tells you the directory doesn't exist.

Again, when you try to untar Celtx.tar.gz, you are trying to untar it from a file location that doesn't exist, so it gives you the same error.

Here is what I mean:
> Quote:
sam@UbiOneCanubi:/$ cd /home/sam/Desktop
sam@UbiOneCanubi:~/Desktop$ ls
Celtx.tar.gz
sam@UbiOneCanubi:~/Desktop$

The output from ls shows that Celtx.tar.gz is in the ~/Desktop directory. (By the way, '~' is a shortcut for your home directory -- in your case /home/sam/ -- For me it would be /home/neil/)

So, in the next block, where you tell tar to extract the file at /home/sam/Desktop/to/Celtx.tar.gz if fails because the file is actually at /home/sam/Desktop/Celtx.tar.gz

> Quote:
sam@UbiOneCanubi:~$ cd /usr/local
sam@UbiOneCanubi:/usr/local$ sudo tar zxf /home/sam/Desktop/to/Celtx.tar.gz
[sudo] password for sam:
tar: /home/sam/Desktop/to/Celtx.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
sam@UbiOneCanubi:/usr/local$ 

Don't worry. You probably got confused by instructions that say things like "/pathway/to/file" For future reference, don't include the "to" :)

Here's what you need to do then:
```
cd /usr/local
sudo tar zxf ~/Desktop/Celtx.tar.gz
cd celtx
./celtx
```

That should hopefully run celtx ('./' before an executable file runs the file).

At this point, you'll have to run it from a terminal. You probably want to set it up to run from an application launcher. If you can't figure out how, say so. I'll try to help.

p.s. Celtx.tar.gz is red because it's a package file. You'll see that directories are blue, and executable files are green in the terminal. It's nothing dramatic.

Good luck!

---

### Post by UbiOneCanubi on 2008-05-04
Halfhaggis thank you :KS You're a champion for holding my hand like this. Fortunately it's finally working for me! I've got a couple of other questions for you though - I'm finding it difficult to find info simple enough to proceed by myself.

First up I would like to create an application launcher. I've tried creating a Custom Application Launcher in my panel by right clicking, then Add to Panel > Custom Application Launcher:
Details:
Type: Application
Name: Celtx
Command: ??? (please help)
Comment: Irrelevant

But my problem is what I should put in the command box.

Second, somehow during my muddling around I have created a folder that I cannot delete. Incidentally it is the unzipped celtx folder. A little padlock has appeared on the top right hand corner of the folder and I'm unable to delete it. Do I need to keep the unzipped folder to keep the programme running or can I delete it? If I can delete it, how do I go about removing the protection that's come to life out of it's own volition?

Once again many thanks for taking the time to walk me through this, it's much appreciated!

Ubi

---

### Post by UbiOneCanubi on 2008-05-04
Haha, I got it! Sweet :)

One thing I changed was the final step of what you listed in your last post.

Instead of
```
cd /usr/local
sudo tar zxf ~/Desktop/Celtx.tar.gz
cd celtx
./celtx
```

I remembered the wiki.Celtx installation directions were a little different and tried that.
```
sam@UbiOneCanubi:/usr/local$ sudo tar zxf /home/sam/Desktop/Celtx.tar.gz
[sudo] password for sam: 
sam@UbiOneCanubi:/usr/local$ sudo /usr/local/celtx/celtx
[sudo] password for sam: 
sam@UbiOneCanubi:/usr/local$ 

```

From there I tried creating the Application Launcher again with the details:
Type: Application 
Name: Celtx
Command: /usr/local/celtx/celtx

Success!

Now I just need to figure out how to make an .svg (which I reckon shouldn't be too hard) and I've got myself a perfectly good shortcut.

Once again halfhaggis thanks a million :) I had a feeling it would be something simple which I would kick myself about. Cheers for not making me feel like more of a retard than I managed to myself :)

If you have any thoughts on the protected folder I would love to hear them.

Ubi

---

### Post by halfhaggis on 2008-05-04
The problem with the directions from wiki.Celtx is that it tells you to run the executable (i.e. /usr/local/celtx/celtx) with sudo. In other words, superuser do.

Why is this a problem? It's a security risk. The superuser has access to all files on the system, and so if the executable is malicious, it could delete critical system files, or install some dodgy application on your system.
This is why, in general, you should always try to run programs as a user with normal privileges so if something dodgy happens, your whole system won't be put at risk.

That's why I say run the executables from the command line with ./

Well done figuring out the command, though. When you run it through the launcher, it won't be as the superuser, so don't worry about that.
Also, you can add a custom launcher to the Applications menu if you like, by using System->Preferences->Main Menu
Select the category you want and click "New Item"

You also don't need to make an svg. Icons for celtx are here if you installed it where you said you did: /usr/local/celtx/icons/
Browse there via the icon selection interface and choose one. It doesn't have to be an svg either.


The protected folder:
I assume you mean this one: /usr/local/celtx/ ?
If you do, leave it alone. Those are all the program files. Celtx is running from there.

If you've also extracted it somewhere else, like somewhere in your home directory, you probably did it with sudo, and that is why you can't delete it as a normal user. 
You only used sudo to extract it into /usr/local/ because root (the superuser account) owns that directory, and user sam doesn't have write permissions there (nor should he).
It isn't necessary to use sudo to extract files from a tarball if you extract them to a directory that your user account owns (in other words, somewhere within /home/sam/).

Tell me the location of the directory if it isn't /usr/local/celtx/

---

### Post by UbiOneCanubi on 2008-05-05
Interesting, so it's something like in Windows the difference between using an administrators account versus a limited account when you're installing programmes? Man, so much new stuff to learn :)

I figured out how to added Celtx to my Applications menu. Thanks for your thorough information!

I also ended up figuring out how to make an icon. I checked out the dimensions of the icon that was chosen by default when I created the Application Launcher. 48 x 48 pixels, and for some reason when I created my first icon it didn't scale properly and I was left thinking there was something other than dimension that mattered. I saved the icon off the wiki.Celtx page and scaled it in GIMP to the proper dimensions and saved it as a .png and it all works well.

The location of the celtx directory is /home/sam/celtx. I also checked /usr/local. The code is below.

```
sam@UbiOneCanubi:~$ ls
celtx         Desktop    Examples  Pictures  Templates
Celtx.tar.gz  Documents  Music     Public    Videos
sam@UbiOneCanubi:~$ cd /usr/local
sam@UbiOneCanubi:/usr/local$ ls
bin  celtx  etc  games  include  lib  man  sbin  share  src
sam@UbiOneCanubi:/usr/local$ 

```

Yup.

Thanks once again. Your help has been invaluable :)

Ubi

---

### Post by halfhaggis on 2008-05-05
> Interesting, so it's something like in Windows the difference between using an administrators account versus a limited account when you're installing programmes? Man, so much new stuff to learn

Yes, only it works better in Linux because it's much easier to escalate your privileges and install something using [FONT="Courier New"]sudo[/FONT] (or it's graphical equivalent, [FONT="Courier New"]gksudo[/FONT]). So people actually use normal user accounts (unlike in windows where it is really annoying to -- I tried once).


To remove the celtx folder in your home directory you can try it with sudo. Make sure you are in your home directory with 
```
cd ~
```

Then remove it with
```
sudo rm -r celtx
```

That should do it.

---

### Post by UbiOneCanubi on 2008-05-05
Haha, you tried only once? I agree that it's tediously annoying, I don't think I tried normal User accounts many more times than that either :)

For me Windows is only more intuitive because I've used it almost my entire computer life. I've got to say though over the past week I can see how and why Ubuntu slays XP in terms of versatility and ease of use (relatively speaking). The entire Ubuntu philosophy is right up my alley too.

I think the only thing stopping Ubuntu is the learning curve that's required to implement and use the operating system properly. Hopefully more electronics companies will follow Dell in offering computers with the OS preloaded, as that's the main block I know that stops people like my parents from using Linux. Once it's in and running I can see very little stopping adopters from dipping their toes in the water.

Your advice worked a treat as always, thanks for being a personal trouble shooter of sorts :)

Ubi

---

