---
title: "&quot;go to directory&quot;  HOW??"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-08-31
HI:) 

I am still trying to learn how to install .tar.gz files.  I think I understand most of it except for what I need to do first. 

After extracting (which I know how to do) I have to open the terminal and **"go to the directory"  **  before I can do the ./install bit.  What do I have to type in the terminal for the directory?  Say I have extracted a file called TRY  to a folder in home/russty/software   So what do I have to type in the terminal to go to TRY?  :confused: 

This may seem a silly question, but I have tried several things, even choosing copy and paste into the terminal, but I am just not getting it right.](*,)   I have read the How to install anything in Ubuntu page but it is just this type of file I am still having problems with.

Russty.

---

### Post by aysiu on 2006-08-31
Are you learning how to install .tar.gz files because you don't know there's a much easier way to install software or because...

1. It's software not available in the repositories
2. It's the absoluting cutting edge version of software that is available in the repositories
3. You just want to learn for fun

...?

If you don't know, there are easier ways to install software: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

In any case, the command you're looking for is *cd*: ```
cd /home/russty/software
```

---

### Post by Carbonfish on 2006-08-31
Russty

You can use the cd command in the terminal to "go" to the directory. (cd stands for "change directory")

In your case, I believe that it would be:

cd /home/russty/software

Give that a try.;) 

KC

---

### Post by desmondo on 2006-08-31
Hi

I'm not sure if this is the answer for which you're looking, but to go to a directory in Linux you use the "cd" command (as in Change Directory):

cd /home/russty/software

Note that if you want to change to an absolute directory, you have to put the root slash "/" at the beginning of the path.  Without this slash, you would be asking to change to a "home" directory located in whatever directory you are currently in.

Please post again if this isn't what you were looking for.

---

### Post by bodhi.zazen on 2006-08-31
> **Russty of Oz said:**
> HI:) 

I am still trying to learn how to install .tar.gz files.  I think I understand most of it except for what I need to do first. 

After extracting (which I know how to do) I have to open the terminal and **"go to the directory"  **  before I can do the ./install bit.  What do I have to type in the terminal for the directory?  Say I have extracted a file called TRY  to a folder in home/russty/software   So what do I have to type in the terminal to go to TRY?  :confused: 

This may seem a silly question, but I have tried several things, even choosing copy and paste into the terminal, but I am just not getting it right.](*,)   I have read the How to install anything in Ubuntu page but it is just this type of file I am still having problems with.

Russty.

I agree with all of the above.

Some help 4 U:

pwd = "print working directory"

In your example I presume you are in the directory "home/russty/software" and want to go to "home/russty/softwarehome/TRY" you can:
```
cd TRY #Relative path

OR

cd /home/russty/software/Try #Absolute path
```

FYI "relative" means relative to where you are now. "Absolute" means starting with / (root).

Thus if you are in the directory "/home/russty" the relative path to TRY is "software/TRY". The abosolute path is still "/home/russty/software/Try".

---

### Post by Russty of Oz on 2006-08-31
Thanks guys!  

Sorry for the delayed reply, I have been lazing on a sunny Aussie beach this afternoon.

Now, that is exactly what I wanted!  So thanks to everyone.  I still have a little problem though.

I am trying to install winmx4linux.  I prefer it to frost/limewire as you don't get all those dud files and sex advertising.  I put in the cd/ bit and it seemed to accept it but when I put in the ./install it says there is no such file or directory.  But there is!  So perhaps I need a bit more help here.  Below is the installation instructions.  So I have put in **cd/home/russty/Software/winmx4linux-3.31-0.1zip_FILES**   and this gets accepted and waits for me to put the next bit in.  So I put in  [B]./install-winmx4linux
[/B]
but it said there was no such file or directory, but there is a winmx4linux folder in there.  And I do have wine installed.

[B]Installation:

- Make sure you have a recent Wine version installed ([www.winehw.com](www.winehw.com)) and also check if you have the .wine user configuration directories.
- Go to a terminal window.
- Go to the directory where you unpacked winmx4linux-3.31-0.1.zip
- Type on the prompt: ./install-winmx4linux
- This should run the script with two times a 5 second break, to let you change your mind.
- WinMX should be started automatically after the script has done his work.[/B]

So can anyone help here?

Russty.

---

### Post by Frank Golden on 2006-08-31
Watchout for case sensitive.
an example: if you want to change to Desktop the command would be in rustys
case [cd /home/russty/Desktop] without the brackets of course.
You can shorten this to cd ~/Desktop for the same result. The ~ symbol
replaces /home/russty in this case. Watch your spacings also in the example Russty of Oz gave above 
cd/home/russty/Software/winmx4linux-3.31-0.1zip_FILES
there should be a space after cd. Probably a typo as this probably would
have generated an error.

---

### Post by Russty of Oz on 2006-08-31
Yes I did leave a space after cd 

My problem is with the ./install bit now.

Russty

---

### Post by Frank Golden on 2006-08-31
> **Russty of Oz said:**
> Yes I did leave a space after cd 

My problem is with the ./install bit now.

Russty
Yeah that's what I thought. Did you unpack that .zip file first?
I don't see where you did.

---

### Post by Russty of Oz on 2006-08-31
Yes I unpacked it, the downloaded file was winmx4linux-3.31-0.1.zip and when I extracted it, I got a folder called winmx4linux-3.31-0.1.zip_FILES. 

Russty

---

### Post by 3rdalbum on 2006-08-31
One of your posts was a bit unclear. Is there a file called "install-winmx4linux" inside the "winmx4linux-3.31-0.1.zip_FILES" folder? Or is it in a subfolder?

Your terminal must be in the directory which directly contains the "install-winmx4linux" file.

---

### Post by toasted on 2006-08-31
Once you open your terminal you have to navigate into the same directory that the file you want to install is located. I think you know this now. To check to see if you are in the correct directory try this:

```
ls
```

That will list everything that is in the directory that you are currently in. If the program you are trying to install is not there, then obviously you are not in the right place yet!

---

### Post by Russty of Oz on 2006-08-31
> **3rdalbum said:**
> One of your posts was a bit unclear. Is there a file called "install-winmx4linux" inside the "winmx4linux-3.31-0.1.zip_FILES" folder? Or is it in a subfolder?

Your terminal must be in the directory which directly contains the "install-winmx4linux" file.

Inside the Software folder is one called /home/russty/Software/winmx4linux-3.31-0.1.zip_FILES

inside this folder is /home/russty/Software/winmx4linux-3.31-0.1.zip_FILES/winmx4linux

inside this folder is /home/russty/Software/winmx4linux-3.31-0.1.zip_FILES/winmx4linux/install-winmx4linux
/home/russty/Software/winmx4linux-3.31-0.1.zip_FILES/winmx4linux/start-winmx
/home/russty/Software/winmx4linux-3.31-0.1.zip_FILES/winmx4linux/fake_windows
/home/russty/Software/winmx4linux-3.31-0.1.zip_FILES/winmx4linux/WinMX.xpm

So, after the cd /home/ etc, what do I do at the next prompt?

Russty

---

### Post by nickbooker on 2006-08-31
To answer your question (whatever directory you're currently in):
```

cd /home/russty/Software/winmx4linux-3.31-0.1.zip_FILES/winmx4linux
chmod +x install-winmx4linux
./install-winmx4linux

```

This should get the installer running.

---

### Post by Russty of Oz on 2006-08-31
Well that seemed to be working, at least the installer worked but then I got this message:

[B]./install-winmx4linux: line 31: cd: /home/russty/.wine/fake_windows/Program Files/WinMX: No such file or directory

[email]russty@russty-desktop:~/Software/winmx4linux-3.31-0.1.zip[/email]_FILES/winmx4linux$ wine: could not load L"c:\\windows\\system32\\WinMX.exe": Module not found
[/B]
So does anyone know what Module not found means?  Perhaps winmx is meant to work on some other form of Linux and is not compatible with Ubuntu?

Oh well, at least I have learnt some things about installing, so that's good.

If anyone can help further, it will be appreciated.

Russty.

---

### Post by bodhi.zazen on 2006-09-01
Just have to ask the obvious: Have you installed and configured wine?

If so, try editing line 31 of "install-winmx4linux" to point to your correct fake_c drive.

---

### Post by Russty of Oz on 2006-09-01
> **bodhi.zazen said:**
> Just have to ask the obvious: Have you installed and configured wine?

If so, try editing line 31 of "install-winmx4linux" to point to your correct fake_c drive.

Yes I have installed wine, and have configured it as Windows XP.

How do I know what the name of the fake c drive is??  

Russty

---

### Post by SentientFluid on 2006-09-01
> **Russty of Oz said:**
> [B]./install-winmx4linux: line 31: cd: /home/russty/.wine/fake_windows/Program Files/WinMX: No such file or directory

~/Software/winmx4linux-3.31-0.1.zip_FILES/winmx4linux$ wine: could not load L"c:\\windows\\system32\\WinMX.exe": Module not found

The first error is obvious and means that at least one of the folders/files in the path wasn't found.  Everything after */home/russty/* is suspect so you can narrow it down by going to that directory and typing **ls**.

Look through the list it brings up for **.wine**.  If it exist then cd into it and ls again until finally you figure out which directory/file doesn't exist.

I believe the second error message is saying that it can't find the WinMX.exe module.  Are you running the WinMX installer from inside Wine or just in Ubuntu?

---

### Post by Russty of Oz on 2006-09-01
When I type ls in, I get the following;

russty@russty-desktop:~$ ls
amsn_received           GoogleEarthLinux.bin  wine_0.9.9-0ubuntu2.diff.gz
automatix.log           Photos                wine_0.9.9-0ubuntu2.dsc
Desktop                 Screenshot.png        wine_0.9.9.orig.tar.gz
Examples                showthread.php        WinMX.desktop-gnome2
firefox-1.5.0.6.tar.gz  Software              WinMX.xpm
googleearth             start-winmx
google-earth            Videos

As for the second question, I don't know.

Perhaps I should give up on this and just use winmx in windows.

Sigh!

---

### Post by bodhi.zazen on 2006-09-01
The directory .wine is hidden. You will not see it unless you use ls -a.

You can shorten the list ls -a will return in ~ with grep.
```
ls -a | grep .wine
```

Then cd .wine and you can use ls in each subsequent directory.

---

### Post by Russty of Oz on 2006-09-01
OK, I did that and got this:
[email]russty@russty-desktop:~/.wine[/email]$ ls
config                      dosdevices  system.reg   user.reg
config-backup-before-winmx  drive_c     userdef.reg
[email]russty@russty-desktop:~/.wine[/email]$

So where does that get me?

Sorry for being so dumb.

---

### Post by bodhi.zazen on 2006-09-01
Not sure. Try this:

In ~/.wine (your current directory)
```
ln -s /home/russty/.wine/drive_c /home/russty/.wine/fake_windows
```

then re-run you install script

Note the space between "drive_c" and "/home/...."

---

### Post by Russty of Oz on 2006-09-01
> **bodhi.zazen said:**
> Not sure. Try this:

In ~/.wine (your current directory)
```
ln -s /home/russty/.wine/drive_c /home/russty/.wine/fake_windows
```

then re-run you install script

Note the space between "drive_c" and "/home/...."

**AT LAST!**

That did get it working.  Now I just have to configure it with my router and I should be OK.

THANK YOU VERY MUCH!  

Russty.:D

---

