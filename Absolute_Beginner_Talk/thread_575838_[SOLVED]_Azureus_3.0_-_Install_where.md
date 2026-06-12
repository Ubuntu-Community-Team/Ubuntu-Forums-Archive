---
title: "[SOLVED] Azureus 3.0 - Install where?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2007-10-14
Hi all,

I downloaded and extracted ver. 3.0 to my home folder. I have Sun jre 6 installed as well. I can launch Azureus by dbl clicking on the file in the azureus folder in my home folder and it works fine. 

This is a less than ideal install tho. I am very new to Ubuntu and moderately new to linux. Where should this and other local install software be installed? I suppose I drop the azureus folder somewhere customary (I don't know where that is for Ubuntu) and then make a symbolic link to it from some bin folder (also customary).  

BTW I have apt-get installed azureus and it put things all over the place. It's all ver2.5 tho and closes immediately after opening. I suspect it's because I have run 3.0 already and the config files it created in my home folder conflict somehow.

Any help on where to put 3.0 so it's available to all users would be appreciated!
Eric

---

### Post by 001100 on 2007-10-14
i think that its already installed to your computer in the azureus folder. I have azureus 2.5 from the add/remove apps. search azures and find the main  folder and then drop the files in it. I would use it but I'm installing ubuntu 7.10 in the next 4 days

---

### Post by nowhere@cox.net on 2007-10-17
Seems no one's interested in this. This led me to post another question in general about the directory structure of Ubuntu and Linux. No one could answer there so I guess it's a topic no one understands. The way we have always done it kind of thing. :confused:

Anyway, to take a guess at answering my own question, I found an ebook that Kinda (very kinda) explained what folders were for what. It seems that the best place for the Azureus package I download and untar would be in usr/share with a sym link to the executable in /usr/bin.

If this is stupid let me know.

---

### Post by jayaramk on 2007-10-18
why download somethink is its present in the repositoreis..... use the synaptric package manager and search for azureus...... and install it!!!

---

### Post by nowhere@cox.net on 2007-10-18
Last I checked it was version 2.5 in repository. I'll check again...

Thanks!
Eric

---

### Post by Soarer on 2007-10-18
The repo version is 2.5.

I guess the reason no one answers is because all the documentation is there if you look for it.

For example: [http://azureus.sourceforge.net/howto_linux.php](http://azureus.sourceforge.net/howto_linux.php) tells you how to install & run it on Linux.

Lots of places will tell you how to create a menu launcher, if that's what you want to do.

---

### Post by nowhere@cox.net on 2007-10-19
I'm sorry but all three posters, while kind to post a response, didn't address the question. The subject CLEARLY states my question. I don't want 2.5, I want 3.0. The software can be downloaded from Azureus' website and you get the runtime java stuff and I can do this.

I didn't ask HOW I asked WHERE and I think you will agree that the docs do NOT explain what are the customary locations for such kind of manual installs since Ubuntu's goal is remove as much of the manual. 

I am obviously in the wrong forums since no one seems to want to discuss Ubuntu and help me learn how it works. Everyone just wants to point me to some doc that walks me through it without explaining the underworkings.

Fine. 

But I pull this quote from the Absolute Beginner's Read me First posting:
> Because so many newcomers to Ubuntu start in this area, the following rules -- taken from the Ubuntu Forums Code of Conduct -- are strictly enforced in this area. These are paraphrased for brevity's sake; you can read the original rule on the policy page.

    * There are no stupid questions (II:1). Everyone was new to Linux at some point.
    * Be polite, respectful (I:1) and considerate (II:6).
    * Try to communicate as clearly as possible (I:10).
    * Give basic instructions, in step-by-step form when necessary (II:14). Try to avoid jargon (II:7).
    * Answers like "STFU", "RTFM" or "Google it" ARE NOT ACCEPTABLE UNDER ANY CIRCUMSTANCES (II:8 ). Those answers will incur warnings, infractions or bans if a staff member feels it is appropriate. This is a cardinal rule of our community.


I would contend that "there is so much documentation out there" is a synonym for "Google it" and please read what it says immediately after that especially when the question isn't even being addressed.

Here is the link you provided:
```
1) Install JRE from here.

2) Extract latest linux package (choice of GTK or Motif) from here

    * To extract the program files from the package, type
          o tar xvjf Azureus_x.x.x.x_linux...tar.bz2
      where Azureus_x.x.x.x_linux...tar.bz2 is the name of the downloaded package. 

3) Change to the azureus directory and run ./azureus to start

    * cd azureus
    * ./azureus

If you get an error message, or want to configure the java exec path, just open the azureus script file with your favorite text editor and edit the given configuration options.

If Azureus does not show up after a minute, you can try starting it manually:

    * GTK:
          o java -cp swt.jar:swt-pi.jar:Azureus2.jar -Djava.library.path=./ org.gudy.azureus2.ui.swt.Main

    * Motif:
          o java -cp swt.jar:Azureus2.jar -Djava.library.path=./ org.gudy.azureus2.ui.swt.Main

4) Please give feedback, if any exceptions were thrown. 
```

Notice this doesn't address my question at all. And if with your experience level, you come up with the wrong search, image what a new guy like me is up against. I don't even know if "directory structure" is the correct term for what I am describing.

Now I don't know what I am doing wrong in posting. I usually spend at least an hour researching and searching before posting but I am getting this kind of response a lot.  

Now, having not gotten the response I was looking for here, I generalized, reposted a rephrase of the question, and got the same kind of answer. Eventually in that thread someone was kind and posted links to a page that rather fully described what each folder in a Linux filesystem is for so this thread is no longer needed.  So I am on my way doing exactly what you think I am not doing and that is reading documentation and trying to learn.

Anyway, I'm sure all posts were done with the intent to help so thank you for taking the time.

Eric

---

### Post by techno-mole on 2007-10-19
i know this has been solved, but i thought i would add my opinion aswell.
i have 3.0 installed, all i did was to create a folder in my home directory called applications, in that i created a folder called azureus and extracted the contents of the download to it, i then copied the frog icon to usr/share/pixmaps and then to create a menu item i went to system - preferences - main menu and under the internet section i created a new item, i chose the frog icon and for the command i browsed to the folder i had created and chose the shell script.
and that works great.
i have a couple of applications running this way and never had any trouble.
you could also try converting the downloaded file using alien, i did that for xdvdshrink, i downloaded an rpm, converted it with alien and installed it that way.
half the reason i do it like this is because im lazy :)
cheers

---

### Post by NiklasV on 2007-10-19
It doesn't really matter where you put Azureus, though I wouldn't put it in the /usr/share directory as you suggested, simply because that's where the azureus installed from the repos are installed. I would put manually installed software that I want to be available system wide under the /opt directory. You could also put it in your home directory if you don't care if it's not available to other users.

If you want to run azureus by typing azureus anywhere in a terminal or run dialog, you could put a symlink in one of the predesignated bin directories (/usr/bin/,/usr/local/bin, etc), though you should make sure it doesn't conflict with the repo installed azureus. (for instance name the symlink azureus3)

Though if you only want to access azureus by clicking an icon there's really no reason to put it in the PATH, just enter the entire path to the binary in the shortcut.

---

### Post by techno-mole on 2007-10-19
not to be rude, but i put azureus in my home folder (maybe i didnt put that in my original post ?) i only put the icon in usr/share/pixmaps, mainly because thats where all the other icons are.
cheers

---

### Post by NiklasV on 2007-10-19
I was actually referring to [email]nowhere@cox.net[/email]'s post (third post) where he suggested that he could put the azureus directory under /usr/share

---

### Post by techno-mole on 2007-10-19
my bad.
cheers

---

### Post by nowhere@cox.net on 2007-10-19
Awesome guys! This is the kind of discussion I was looking for. 

I tend to like to keep programs out of my home dir since they get mixed in with the data bnut in fact that is exactly where it is now.  I do want it available to other users eventually as well.

 I like the /opt idea. I didn't really know what this folder was for. I read another link someone sent me and it is for "optional" software. Sounds like a great place to me.

Thanks for the hint about /usr/share/pixmaps too as I didn't know about this folder. I will have to research what that's all about too...

So my NEW plan with all your suggestions is /opt/azureus3 with a symlink to the executable in usr/local/bin. Does this sound more like what a knowledgeable sys admin would do? :)

Again thanks for the discussion. I learned way more from just these couple messages!

---

### Post by fluzao on 2007-10-19
> **nowhere@cox.net said:**
> Hi all,
(...)
It's all ver2.5 tho and closes immediately after opening.
(...)
Eric

Eric, this is an known bug. In order to sort that out, you must delete the contents of /home/.azureus/log/. It should open fine. Repeat the procedure when it closes immediately after opening again.

---

### Post by nowhere@cox.net on 2007-10-30
Thanks Fluzao!

---

