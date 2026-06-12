---
title: "Why is it so it so complicated to install apps on Ubuntu (linux)?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by diargasm on 2007-05-02
Is it for practical issues like security?  Is there a philosophical reason why?

---

### Post by enzobelmont on 2007-05-02
what are you talking about???

is the easiest distro for that.

maybe you want to compile your own apps?

please be more explicit.

sorry my english... :)

---

### Post by Bartender on 2007-05-02
If you have broadband it's ridiculously easy to install apps from the repositories.

---

### Post by darkworld on 2007-05-02
Its not difficult once you get to grips with it. Especially if you look in the right places.

[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

and

[http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")


Its the way its evolved.

---

### Post by sohaibma on 2007-05-02
which OS did you compare Ubuntu to reach your conclusion that installing apps in ubuntu is complicated.
I'm pretty sure ubuntu is simpler than all the other linux distros out there.

---

### Post by fakie_flip on 2007-05-02
Not all apps are hard to install. It depends. If the software you are looking for is in the Ubuntu repositories, then it will be easy to install using the "Add/Remove Programs" or Synaptic. I suggest you learn and use Synaptic until you become more familar with Ubuntu and Linux.

---

### Post by diargasm on 2007-05-02
> **sohaibma said:**
> which OS did you compare Ubuntu to reach your conclusion that installing apps in ubuntu is complicated.
I'm pretty sure ubuntu is simpler than all the other linux distros out there.

I'm comparing it to windows.  I thought it was just me being a newbie, but it seems very difficult to get apps working that are not in "add/remove" list.

---

### Post by darkworld on 2007-05-02
Hey peeps they are right. This is the newbie section.

Of course its easy...for us...we are already there!

Imagine....some poor soul could have just run up a live distro cd and found this forum...maybe there whole life has been Windows.........of course it would be difficult!

Making the transition is difficult but very worth it.

---

### Post by darkworld on 2007-05-02
> **sohaibma said:**
> which OS did you compare Ubuntu to reach your conclusion that installing apps in ubuntu is complicated.
I'm pretty sure ubuntu is simpler than all the other linux distros out there.

Mandriva is pretty easy. In fact I would say using urpmi is even easyier.

---

### Post by tuxcantfly on 2007-05-02
> Mandriva is pretty easy. In fact I would say using urpmi is even easyier.

if it's command-line you like, you can do it fine with apt-get in ubuntu:

sudo apt-get install applicationname

or even easier, add/remove applications or synaptic, (litterally) 3 clicks and you're done installing

as for compiling stuff from source, that's just up to the packager; hopefully he made an ubuntu/debian package, and if he didn't, you'll have to compile from souce (newbie-unfriendly) but that's the way it is on all the linux distros; if no rpm package is availalbe for mandriva, then it'll be the same there too

---

### Post by Bartender on 2007-05-02
> **darkworld said:**
> Hey peeps they are right. This is the newbie section.

Of course its easy...for us...we are already there!

Imagine....some poor soul could have just run up a live distro cd and found this forum...maybe there whole life has been Windows.........of course it would be difficult!

Making the transition is difficult but very worth it.

Well, I guess you're right but the original post was a bit combative and uninformed at the same time.  Not a good combination.

What is it you want to do?  Music?  Graphics?  E-mail?  Tell us what you're trying to do and chances are we can point out some programs to download via Synaptic. 

Synaptic is only hard once.  The 'buntu group has a great catalogue of applications ready for downloading.

---

### Post by enzobelmont on 2007-05-02
use adept in kubuntu or synaptic in ubuntu or apt-get install <package_name> on command line.

it is easier than beat a blind man with a baseball bat.

sorry my english... :)

---

### Post by MindRiot on 2007-05-02
I feel ya!

I don't think installing apps through Add/Remove or Synaptic is any easier than installing programs in Windows XP.  All you do in Windows is download the file and double-click to run the installation. Pretty damn easy, and the method I prefer. Basically, that's what Add/Remove and Synaptic do anyways. In either case, the installation is automated and easy. The positive side to the Ubuntu repositories is the apps are "supposedly" safe and prevent you from installing apps that pose dependency problems..

There are additional steps you often must take to install apps in Ubuntu/linux that you do not necessarily have to do in Windows.

1. I have never had to compile a program from source to install that program in Windows because the new kernel broke the application available in the Ubuntu repositories.

2. In Windows XP, I've never faced an installation scenario that required entering a series of commands in Run or at the MSDOS prompt to install a program.

3. To install using apt-get, Add/Remove, or Synaptic/Adept, you must locate and add the necessary repository to /etc/apt/source.list.

4. Obtain security key (Not always easy)

5. I've never had to download headers to install device drivers in Windows.

6. Often times it is necessary to change the permissions on the archive or script.

7. Sometimes you need to manually edit environmental variables, and other system configuration files.  I've never once had to hack the registry in Windows XP to tell the system where to find a program I just installed. However, that's not to say there's no need to hack the registry or edit config files in Windows XP. 

8. usr/X11R6/sbin and other folder names in the filesystem are not intuitive like Program Files\<app name>. Often I need to open Synaptic, find the app I installed and click properties to find where the program was installed. It's possible to install an app in Linux that doesn't create a shortcut in the Applications menu and requires you to manually create a launch shortcut.

9. Often you need to write a script to load a program on startup. In Windows XP, you drag and drop the program in the startup menu. Sure, you can write batch files, but I've never had to.

10. Game patches and updates that are released only in a Windows installer. Like UT2004 maps packed in UMods. How do you extract the files without using WIndows or wine?

11. A different terminology is used by each OS. Dealing with new terms or new ways of saying the same thing can lead to confusion. I think windows speak is more intuitive, but that's probably just a matter of taste. 

12. The fact that I have to read a Howto or visit this forum is reason enough to justify the claim that some apps are harder to install in Ubuntu than Windows.

The truth is that with Linux there are often additional steps you must take to install an application if you don't use apt-get, Add/Remove, Easybuntu/Automatix2, or Synaptic/Adept that are not necessary when installing programs in Windows.

Yet, I'm addicted to Ubuntu nonetheless, go figure.

---

### Post by Gaunty on 2007-05-02
It's hard to compete with double clicking on an MSI or Setup.exe file.

One thing going for linux though; you hardly ever get asked to provide the setup with installation locations and loads of other information that you always select the default values to.

---

### Post by carl0ski on 2007-05-02
> **diargasm said:**
> I'm comparing it to windows.  I thought it was just me being a newbie, but it seems very difficult to get apps working that are not in "add/remove" list.

You'll find a more detailed variety list of programs in the uncut Synaptic Package manager in System>Administration


thats weird i always find the point and click approach of a RPM or Deb file was easier since it didnt ask dozens of questions.

Did you know that Symantec made this Setup.exe?
Did you know that Nullsoft developed the installer in this Setup.exe?
Where should i really copy the files in this setup.exe?
I'm confused do you want a custom, Express or Complete setup?
Once installed should i do A, B, C, D, E or F?
Argh i've finished would you like to register online?

---

### Post by efflux on 2007-05-19
Once you're used too it it may seem easy but compare to downloading a file and dragging it into your applications folder, double clicking and the program starts. That's how OSX does things. Installing software on Macs is absurdly easy. There are no dependency or .dll issues to deal with at all. It's an unfortunate fact in some ways but this kind of simplicity for the end user is why I consider my Mac system to be in a league way ahead of Windows or Linux.

---

