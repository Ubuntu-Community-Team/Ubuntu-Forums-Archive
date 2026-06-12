---
title: "So, how does Linux WORK?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by nathanscottdaniels on 2008-03-25
This is all very strange.  How/where does linux store applications?  How come I cannot find the .exe (or whatever the Linux equivalent is) file for thunderbird?  Where are all my drives?  Where is the nice user-friendly My Computer that is so invaluable in Windows?  Where is the nice  user-friendly My Network Places that is so invaluable in Windows?  How come almost every folder name is only 3 letters long?  AHH!  Help!  :confused:

---

### Post by sports fan Matt on 2008-03-25
You have several questions there..Try not to be so frantic and maybe ask them one at a time like:

Where are all my drives?
Where is the nice user-friendly My Computer that is so invaluable in Windows? and so on.  I would just wait for all these questions to be answered...:)  They will, in time :)

---

### Post by northern lights on 2008-03-25
The (by default) upper panel gives you all you're asking for -

You can check your network settings at "System>Administration>Network" the "Places" menu should give you an overview of your entire filesystem ("my computer").

Thunderbird may be launched via the (most intuitive) command "thunderbird" - from the terminal, the "Alt+F2" dialog or any shell.

--> Just because Windows is installed on most computers, people assume the way windows handles things is the way computers handle things and thus Linux is not intuitive - mistaken...

---

### Post by steveneddy on 2008-03-25
This is all very strange.

 How/where does linux store applications?
[B]Most are in the /bin folder.
[/B]
 How come I cannot find the .exe (or whatever the Linux equivalent is) file for thunderbird?
**Look under Applications, Internet, Thunderbird. If you have Thunderbird installed, that is.**

 Where are all my drives?
[B]Places, Computer
[/B]
 Where is the nice user-friendly My Computer that is so invaluable in Windows?
**Either Places or your /home folder**

 Where is the nice user-friendly My Network Places that is so invaluable in Windows? 
**Places, Network**

How come almost every folder name is only 3 letters long?
**Because**


You know, it's OK to press buttons and try a look around at the top buttons. 

Most people will play with it for a while. There is very little on the desktop as opposed to Windows where there is crap everywhere.

Please[ look here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy").

---

### Post by LlantoSubterraneo on 2008-03-25
Oh man are u in for a ride ! You're lucky u got into linux at this time, before it was alot harder to understand. I recommend u buy books and learn on your own. It is a great experience and it will become an addiction, control and tune almost everything in the system !!

---

### Post by Wolfan on 2008-03-25
I was just like you about a month or so ago when I decided to give this "whole Linux thing" a shot.  My advice is similar to steveneddy and I agree with him very much.  Just click things , and feel the Zen, take a deep breath and just sort of let certain things be. You won't understand it all at first but that's OK.  I promise in short time, if you are willing to learn, it starts to make a lot more sense then Windows ever did. 

Okay maybe a bit romantic...but welcome to the club, LOL :lolflag:

---

### Post by microfi on 2008-03-25
Well, in my opinion (because it happened to me too), those who were familiar with Windows will find the Linux a little odd, but with some time, you'll certain love this free operating system. Ubuntu is one of the most user-friendly distributions available. Most applications you need are in the Add/Remove panel just in the start menu, and your beloved "My Computer" can be easily accessed in Places > Computer.
The filesystem structure of the root drive looks more like an internet server. At first you could think it's messy and inefficient, but the fact is that Linux is pretty organized: it stores binaries in /bin/ or /usr/bin, shared files in /usr/share, etc... (Windows puts everything in its "Windows" folder or "Program Files").
Linux can handle a lot of "executables": the binaries, compiled with C (gcc, make), Python, Java, etc (though the last ones are interpreted)...
In Windows, the kind of the file is determined by its extension (executables are ".exe", video files are ".avi", etc..), and in Linux it's defined by MIME Types (text documents are "text/plain", etc..). So you can rename files as you want.
I haven't browsed the network in Linux yet, but I guess it's necessary a program called SAMBA if you want to connect to Windows network (also, "My Network Places" can be accessed by Places > Network).

Well, I hope it helps a little. Don't give up Linux! With a little effort and patience you'll never want to go back for Windows.
Filipe.:)

---

### Post by sumguy231 on 2008-03-25
> How/where does linux store applications?
It keeps applications in pieces all over the place, but the executables (like .exe files) themselves are almost always in /usr/bin. /bin is generally for binaries that came with the system.

> "How come almost every folder name is only 3 letters long?"
They came up with that naming convention in the 1970s when the Teletype keyboards they used could nearly break your fingers from trying to type on them.

---

### Post by Rickydd on 2008-03-25
haha, this is tipicial windows-linux turning user~

what can i do at that time?

i try to forget everything and back to the time of DOS 6.22

and this is a all new system,and enjoy the different~

everything general you can find on the wiki page , don't worry

---

### Post by nathanscottdaniels on 2008-03-25
Sorry if I came across as stupid.  I know tons about computers, I just lack the phd required to learn what operating systems do.

My question is not how I find thunderbird, but where in this poorly organized file system is the thunderbird file located?  It is not in bin.

Do file extensions exist in linux?  Nearly all the files in the bin folder are extension-less.

EDIT:  Jeez.  You guys respond too fast for my replies to be current!

---

### Post by Witling on 2008-03-25
I'll echo what some of the other posters have said. I'm very, very new to Linux. And I come here with a fairly good knowledge of Windows. Linux is different and learning new skills is, for me, frustrating. I mean, come on, you know that this operating system has to have this, e.g., "find this file," function. But where is it? For my part I find Linux very well thought out. Different from what I'm used to, but very well thought out.

---

### Post by frank002 on 2008-03-25
Welcome to Linux. I myself am a newbie and still learning. After using Windows for 10 years, I was used to doing things the Windows way. Switching over to Linux includes a learning curve but .....so what? I used to spend hours every weekend running Symantec Antivirus, Defrag, Scandisk, Spybot Search & Destroy, Adware.........Not any more. At the top left of your desktop you will see Applications   Places   System. Explore these and a lot of your questions will be answered. Good Luck.

---

### Post by microfi on 2008-03-25
Well, It's advisable to learn something about Linux before saying it's poorly organized.
You could start easily: browse the folders, run some apps, get familiarized with the environment and read something on the Internet.

If you're like me, soon you'll be loving the ability for tuning your Linux!
Filipe.

---

### Post by nathanscottdaniels on 2008-03-25
What's MIME?

---

### Post by bilal.17 on 2008-03-25
well actually the so called ".exe" or binary is in the /usr/bin

where you can find  thunderbird

---

### Post by LaRoza on 2008-03-25
> **nathanscottdaniels said:**
> Sorry if I came across as stupid.  I know tons about computers, I just lack the phd required to learn what operating systems do.

My question is not how I find thunderbird, but where in this poorly organized file system is the thunderbird file located?  It is not in bin.

Do file extensions exist in linux?  Nearly all the files in the bin folder are extension-less.

EDIT:  Jeez.  You guys respond too fast for my replies to be current!

Poorly organized? It is very organized.

It is in: /usr/bin

File extensions do exist, but they don't mean much.

In Windows, file extensions are used to determine what the file is and if it is executable. If you get a copy of the "I love you" virus, you will see it is plain text, with the extension .vbs. If you double click it, Windows will run it, because ".vbs" means it is a VB Script. If you change it to .txt, it will open in notepad, if you change it to .exe, it will try to run it. Most insecure and silly.

---

### Post by microfi on 2008-03-25
To understand MIME-types, take a look on Wikipedia:
[http://en.wikipedia.org/wiki/MIME]("http://en.wikipedia.org/wiki/MIME")

---

### Post by LaRoza on 2008-03-25
> **nathanscottdaniels said:**
> What's MIME?

[http://en.wikipedia.org/wiki/MIME](http://en.wikipedia.org/wiki/MIME)

---

### Post by LaRoza on 2008-03-25
> **microfi said:**
> To understand MIME-types, take a look on Wikipedia:
[http://en.wikipedia.org/wiki/MIME]("http://en.wikipedia.org/wiki/MIME")

@OP, you see we both gave links to wikipedia. You will find that wikipedia is a pretty good resource for such things.

---

### Post by Dr Small on 2008-03-25
Want to find out where Firefox is? This is the simplest way:
```
drsmall@darkghost:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/X11R6/bin/firefox /usr/bin/X11/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz

```

---

### Post by sumguy231 on 2008-03-25
Luckily if you know the command to launch Thunderbird, there is a command to find it. In the terminal, use the which command to find where an application is, like so:
```
sumguy231@zorak:~$ which firefox
/usr/bin/firefox
sumguy231@zorak:~$ 

```

Files can and often do have file extensions in Linux, but file extensions aren't as important as they are in Windows, since most things just look at the file type to find out what kind of file it is.

---

### Post by microfi on 2008-03-25
Yes, we did it.. :)
Thanks for the "whereis"! I didn't know about it!

---

### Post by sumguy231 on 2008-03-25
> EDIT: Jeez. You guys respond too fast for my replies to be current!
I know what you mean, man. This thread is making me dizzy trying to keep up!

---

### Post by LaRoza on 2008-03-25
> **Dr Small said:**
> Want to find out where Firefox is? This is the simplest way:
```
drsmall@darkghost:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/X11R6/bin/firefox /usr/bin/X11/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz

```

Here is a guide to the basics of the directory structure: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

It is very easy to follow once you get used to it. Everything in Windows is all over the place, and difficult to find.

---

### Post by microfi on 2008-03-25
Yeah, everytime I type F5 a couple of threads appear!
Now, with some experience in Linux, I do prefer it's directory structure: it's cleaner and more rational than Windows!

---

### Post by SunnyRabbiera on 2008-03-25
Poorly organized?
Hardly, linux is just different then how windows is laid out.
Me I think linux is pretty well organized and in some ways it can be more organized then windows is.

Here are some basics:
My Computer= Computer, easy to figure out
Program files= usr/bin or sometimes usr/lib, the thunderbird file is usually in usr/bin
My Documents= Home

Linux is based around the unix layout, they share a lot of common directories with eachother.
Here is a good guide to a unix or unix like filesystem:
[http://www.freeos.com/articles/3102/]("http://www.freeos.com/articles/3102/")
BSD and Mac OSX share a similar filesystem

---

### Post by misterhead on 2008-03-25
Everything in Linux is right where you would expect it to be... once you realizewhy it should be there.:)

---

### Post by sumguy231 on 2008-03-25
Mac OS uses the same basic filesystem layout under the hood, but it hides it from the user in Finder. You can see everything in the terminal though. I don't really have an opinion one way or the other on Linux vs. Windows here, unless you count non-NT based Windows releases where everything was in really stupid places and applications thought it was a great idea to just dump things in the root directory.

---

### Post by tango_ninja on 2008-03-25
Linux is incredibly well organised. It is different than windows and might take some getting used to but you will enjoy it more after a little bit of work....

One note, it's not easier....everyone always says that Linux is easier and everything just_works...well that's not true. It's probably MORE difficult to learn and understand and control, and everything DOESN"T just work....you really need to play around.

However, once you do you will enjoy the freedom :)

---

### Post by steveneddy on 2008-03-25
> **nathanscottdaniels said:**
> Sorry if I came across as stupid.  I know tons about computers, I just lack the phd required to learn what operating systems do.

My question is not how I find thunderbird, but where in this**[COLOR="Red"] poorly organize[/COLOR]**d file system is the thunderbird file located?  It is not in bin.

Do file extensions exist in linux?  Nearly all the files in the bin folder are extension-less.

EDIT:  Jeez.  You guys respond too fast for my replies to be current!

Poorly organized? Maybe you meant a file system that you aren't familiar with, right?

Don't compare this to Windows. It is totally different.

You are here because you wanted different, here it is. 

Will it be the [COLOR="Red"]red pill,[/COLOR] or the [COLOR="Blue"]blue pill[/COLOR]?

You be the judge, Neo.

Um, do you have Thunderbird installed?

Silly question, but I had to ask.

Did you look at the link I told you to read?

---

### Post by MeTylerDurden on 2008-03-25
C'mon Bill, I want you to hit me as Hard as you Can!



     :):^o:^o

---

### Post by nathanscottdaniels on 2008-03-25
Yes yes I have TB installed.  I was looking in the /bin and not the /usr/bin for it (which is still not where it is, it is in /usr/lib for whatever reason)

I am a bit puzzled as to why "thunderbird-bin" is not executable like it's MIME says in properties but the "thunderbird" script is

---

### Post by Mr. Picklesworth on 2008-03-25
Out of curiousity, why on Earth are you looking for the Thunderbird binaries?

One thing to note regarding organization is that any desktop application like Evolution, Thunderbird, Firefox, OpenOffice, or Appearance preferences has what is called a .desktop file. That file tells the system how to execute the program, what the program can do, and really anything else important about that program. Many programs place a .desktop file somewhere in the file hierarchy (I forget where, but that is essentially so it appears on your main menu). Any of your own launchers, screen saver themes, places, etc. are defined with .desktop files.
Long story short, that file is very much "the program" ;)

Edit:
Global location for end-user software's .desktop files, of the type you open directly from the menu, is /usr/share/applications

---

### Post by MRiGnS on 2008-03-25
> **nathanscottdaniels said:**
> Yes yes I have TB installed.  I was looking in the /bin and not the /usr/bin for it (which is still not where it is, it is in /usr/lib for whatever reason)

I am a bit puzzled as to why "thunderbird-bin" is not executable like it's MIME says in properties but the "thunderbird" script is

Applications are spread over multiple directories, the libraries of thunderbird are located in /usr/lib

You can probably run the thunderbird-bin by typing:

```
./thunderbird-bin
```

while being in that directory.

Still it seems weird doing that.

---

### Post by koresho on 2008-03-25
That's what I am wondering. After you install the package, you should only have to go to the Applications menu on the upper left hand corner of the screen. It will either be in the Internet or Office section- I don't have it installed so I don't know, personally. 
If you don't find it there then it has not been installed correctly. Open the Add/Remove panel by clicking "Applications > Add/Remove..." and search for "Thunderbird". Check the box on the left of the Thunderbird entry and click "Apply" on the lower right hand corner of the panel. The app will automagically download all the required packages and install them, letting you know when it is done. Feel free to mess around with the general settings after that... 
While you are at it, install "ccsm". That is where you get your crazy compiz-fusion effects...

---

### Post by nathanscottdaniels on 2008-03-25
> **Mr. Picklesworth said:**
> Out of curiousity, why on Earth are you looking for the Thunderbird binaries?

One thing to note regarding organization is that any desktop application like Evolution, Thunderbird, Firefox, OpenOffice, or Appearance preferences has what is called a .desktop file. That file tells the system how to execute the program, what the program can do, and really anything else important about that program. Many programs place a .desktop file somewhere in the file hierarchy (I forget where, but that is essentially so it appears on your main menu). Any of your own launchers, screen saver themes, places, etc. are defined with .desktop files.
Long story short, that file is very much "the program" ;)

The answer is: CURIOSITY!  It started out with me trying to get TB to run a different profile which I figured out.  Now I am just curious.:|

---

### Post by steveneddy on 2008-03-25
Please read this to understand faster/better/fully

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

The official Ubuntu Guide

---

### Post by Tyke91 on 2008-03-25
hehe :) just a tip, an average user should not have to mess around with anything owned by root, if it is in /usr/bin then it should be accessible to everyone, since that file is owned by root and not a specific user. i.e, any of your users should be able to type 
```
thunderbird
``` to get thunderbird up. if it's not in the menu, go to System>Preferences>Main Menu and select show thunderbird :)

---

### Post by SunnyRabbiera on 2008-03-25
> **nathanscottdaniels said:**
> Yes yes I have TB installed.  I was looking in the /bin and not the /usr/bin for it (which is still not where it is, it is in /usr/lib for whatever reason)

I am a bit puzzled as to why "thunderbird-bin" is not executable like it's MIME says in properties but the "thunderbird" script is

Yeh both firefox and thunderbird have their main files in usr/lib they are just odd that way though there are other apps that have their main files there too.

---

