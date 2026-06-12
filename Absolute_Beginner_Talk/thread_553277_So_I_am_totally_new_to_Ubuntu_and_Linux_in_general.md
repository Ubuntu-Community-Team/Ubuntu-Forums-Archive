---
title: "So I am totally new to Ubuntu and Linux in general."
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by primeribs on 2007-09-17
So, as the title says, I am a total newbie to Ubuntu (and Linux.) While I have been curious about it for a while, I finally took the dive this in weekend, and have been fooling around with it to get the hang of it. But there are a few roadblocks I have run into. Think anyone would be interested in helping me out..? Heres some questions (if the questions/thread shouldnt be here, just say so, and Ill take it elsewhere)

1) Installing Java?  I downloaded JRE off the Sun Microsystems website (not the RPM one, but the self extracting file, for linux of course) and as I have come to realise, I cant just double-click it and have it install. Up came the text editor saying:

Could not open the file /home/dearth/Desktop/jre-6u2-linux-i586.bin.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Then it gives me the option to retry or cancel, or change the character coding, which I dont think will help. Well, I looked at the Sun Microsystems website where I got the download and checked out the how to install page. That just lead me to more questions. Like what is su in the terminal? (Or sudo? I have seen that at other sites too) But I tried typing in su at the terminal then hitting enter, then my password, or account password (which, so far, i am the only account on this computer, so wouldnt that make me able to type in the password?) Either way.. I wasnt able to type anything in the terminal until I hit the Enter key, but even then, when I typed in the password for my account, it wouldnt work. So basically everything after the first step was a nogo for me. So Im stuck here.. And was wondering if anyone would be willing to help me out with this, if possible, with a highly detailed explanation, then I could probably get this working.. Thanks

Heh. Sorry if I seem a tad new, Im just..kinda totally clueless. And theres more questions I have.. this is just first on my priority list. Thanks for any and all replies. And if you think theres something I need to know, feel free to randomly just say it.

---

### Post by w4ett on 2007-09-17
Here is the wiki you need:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Both Java and flash are available via Synaptic Package Manager.

---

### Post by mlentink on 2007-09-17
Java can be installed a bit easier than that. In you Applications menu (top-left) there's an option "Add/Remove programs". In it, search for 'Java', select the newest version and click 'Apply'.

---

### Post by edaniel on 2007-09-17
To execute an administrative command, or one that needs "root" rights in the terminal, you type:

sudo <command> 

It will prompt you for the administrator password you set when you installed.

If you need Java you can install it through the Applications menu or the Package Manager inthe Administration menu,  I believe. (Not on my Ubuntu machine right now).  I installed it last month and I don't think I had to use the terminal at all.

---

### Post by olieviya on 2007-09-17
First off welcome and I hope you have fun!

Ok, installing new programs should always be primarily through apt-get/aptitude/synaptic/etc since those places make it much easier to install and also you are sure of what you are doing.
Search for "jre" or "java" in Synaptic to see what I mean.

As you are new to this I'm guessing you feel slightly timid when it comes to the command line/terminal aspect of things (don't be!) but as people have mentioned above you don't even need to touch the command line when using Synaptic, which incidentally can be found in System > Administration > Synaptic Package Manager.

---

### Post by dark_harmonics on 2007-09-17
Yea i ran the java installer the manual way and it really doesnt give you anything that the approved one in the add/remove does. I had a website that wouldnt work but it was the media player's fault. 

It was the the sirius online player. I figured out that it was totem so i removed its plugin with:

sudo apt-get remove totem-mozilla

And then i installed mplayer with 
sudo apt-get install mozilla-mplayer

Now sirius plays great! :)

Turns out the java from the add/remove was fine so i would agree with the above posters.

---

### Post by primeribs on 2007-09-20
Heh, sorry for the delayed reply (dont wish to look rude, just have been busy with real life stuff ranging from school to extra curricular activities.) But thanks for all the responses guys! I *believe* I have Java installed now, though I havent tested it yet, probably will after I finish this post.. but the next thing(s) I were hoping to try and do were 1) Figure out how to create shortcuts  and then I was hoping to getting Sauerbraten (Cube 2) installed, and give that a shot with linux. So basically, What I wanted to try and do originally was try installing Cube 2, but I couldnt just download and install the files I got (nor could I find the files in neither add/remove programs, or the synaptic package manager) but I have one file downloaded to my desktop - is there any way I can open with a package manager to install? 

Once again, thanks to the guys who have responded to my first question - your answers were very thorough and I was able to figure it out quite quickly. And I look forward to any more responses. And sorry in advance if it takes some time to reply too, heh.

---

### Post by Sayers on 2007-09-20
Yeah, Expect things to be easeir than they should be :)

---

### Post by RedSquirrel on 2007-09-20
With regard to sudo, this document is helpful:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

