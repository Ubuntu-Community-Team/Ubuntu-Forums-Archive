---
title: "Copy Paste Issues with Gutsy  - Help"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by ajgoyt on 2008-01-29
Hello just installed Gutsy and I somewhat new to linux, I am trying to install HandBrakeGTK from this post - [http://ubuntuforums.org/showthread.php?t=571637](http://ubuntuforums.org/showthread.php?t=571637)

The problem is when I try to copy the HandBrakeGTK file to /usr/bin I get the following error

jay@UltimateP4:~$ cp HandBrakeCLI /usr/bin
cp: cannot stat `HandBrakeCLI': No such file or directory
jay@UltimateP4:~$ 


Or if i try sudo before cp i get 

jay@UltimateP4:~$ sudo cp handBrakeCLI /usr/bin
Password:
cp: cannot stat `handBrakeCLI': No such file or directory
jay@UltimateP4:~$ 

What am i doing wrong:(

Thanks
AJ

---

### Post by iansane on 2008-01-30
I can't tell by your post. vision is going bad I guess. Is there a space between handbrakeCLI and /usr/bin? There should be. Also if it is a directory put a -r after cp.

---

### Post by brettg on 2008-01-30
The file does not exist (with that spelling) in that location.

Do ls -al and confirm that the file is there.

If it is you might be spelling it incorrectly (using l in place of I for example)

If in doubt highlight the filename in the ls output and copy it to the clipboard, then paste it back at the bash prompt

---

### Post by ajgoyt on 2008-01-30
> **iansane said:**
> I can't tell by your post. vision is going bad I guess. Is there a space between handbrakeCLI and /usr/bin? There should be. Also if it is a directory put a -r after cp.

Hello - Yes there is a Space between HandBrakeCLI and /user/bin


Yes it's the /user/bin dir isn't that root protected?  What is the a-r mean writable?

---

### Post by ajgoyt on 2008-01-30
> **brettg said:**
> The file does not exist (with that spelling) in that location.

Do ls -al and confirm that the file is there.

If it is you might be spelling it incorrectly (using l in place of I for example)

If in doubt highlight the filename in the ls output and copy it to the clipboard, then paste it back at the bash prompt

Hi yes I tried the copy paste method - Um the file is extracted to a folder on my desktop - could that be the problem or is it because I have to be root to copy into /usr/bin?

---

### Post by oedha on 2008-01-30
if the files on desktop......so you sopposed to type
sudo cp /home/username/Desktop/yourfile /usr/bin

regards;
~E~

---

### Post by ~LoKe on 2008-01-30
```
cd ~/Desktop && sudo cp -R HandBrakeCLI /usr/bin
```
That should work.

---

### Post by ajgoyt on 2008-01-30
> **oedha said:**
> if the files on desktop......so you sopposed to type
sudo cp /home/username/Desktop/yourfile /usr/bin

regards;
~E~

E - you the man It Worked:)

Now I need to follow the rest of the instructions for installing Handbrake.....


Thanks
AJ

---

### Post by ajgoyt on 2008-01-30
E - Thanks again now I have a new problem, it appears that i do not have a bin /home/username/.config folder?  see down below in red....... 

Any ideas do I need to create a /home/username/.config folder?

:(



Here's what I did to get the GUI going on Gutsy...
-Download linux binary from Handbrake site
-Extract then copy HandBrakeCLI to /usr/bin
-Download HandBrakeGTK from here [http://sourceforge.net/projects/handbrakegtk](http://sourceforge.net/projects/handbrakegtk)
-**[COLOR="Red"]extract, goto extracted directory, goto bin directory, copy HandBrake directory to /home/username/.config[/COLOR]**
-chmod 0755 HandBrakeGTK.exe
-copy the HandBrakeGTK.exe to where ever you want to run it from
-sudo apt-get install mono
-sudo apt-get install mono-devel
-sudo apt-get install gtk-sharp
-run 'mono ./HandBrakeGTK.exe' to start the gui
Worked for me.

---

### Post by macogw on 2008-01-30
you can just type "mkdir ~/.config" to make that directory.

---

### Post by ajgoyt on 2008-01-30
> **macogw said:**
> you can just type "mkdir ~/.config" to make that directory.

macogw do you think thats what the poster did? 

just asking do you have that folder on your Gutsy?   :)

---

### Post by macogw on 2008-01-30
It must be what they did.  That's the only way to make a directory.  And no, I don't have it because I don't use that program.  It's not a default directory.

---

### Post by oedha on 2008-01-30
if you want to make a directory.....
macogw has answered it
or
sudo mkdir /home/.config

~E~

---

### Post by ajgoyt on 2008-01-30
> **macogw said:**
> It must be what they did.  That's the only way to make a directory.  And no, I don't have it because I don't use that program.  It's not a default directory.

Hmm it says the file exsists - jay@UltimateP4:~$ mkdir /home/jay/.config
mkdir: cannot create directory `/home/jay/.config': File exists
jay@UltimateP4:~$ 


I searched my file system for that folder/file and found nothing!

Thanks for your help so far...

AJ

---

### Post by oedha on 2008-01-30
you have to use sudo --> sudo mkdir /home/jay/.config ( if you want to make it but )
are you sure you dont have that folder ?
cos i have that folder.....and consist of gtk, compiz and others
check from terminal by type :--> ls -la

~E~

---

### Post by ajgoyt on 2008-01-30
> **oedha said:**
> you have to use sudo --> sudo mkdir /home/jay/.config ( if you want to make it but )
are you sure you dont have that folder ?
cos i have that folder.....and consist of gtk, compiz and others
check from terminal by type :--> ls -la

~E~

It's there

drwx------  3 jay  jay     4096 2008-01-28 21:27 .config

So is it hidden?  do i have to enable file view or something?

Thanks E

---

### Post by oedha on 2008-01-30
from nautilus you can see it by
places - home folder
then : view - show hidden files

but you can't copy a file onto it ( unless you change the permission mode )

if you want to copy a file onto it...better for you to do it from terminal
sudo cp /home/jay/yourfile /home/jay/.config

~E~

---

### Post by ajgoyt on 2008-01-30
> **oedha said:**
> from nautilus you can see it by
places - home folder
then : view - show hidden files

but you can't copy a file onto it ( unless you change the permission mode )

if you want to copy a file onto it...better for you to do it from terminal
sudo cp /home/jay/yourfile /home/jay/.config

~E~

Ahh thats it........ the Files were hidden now i will just try a simple copy paste - If that don't work i will try the Terminal.

Thanks

---

### Post by ajgoyt on 2008-01-30
E well i followed the direction,  it just wont it think about starting - You know there is a Deb file for this application - But it errors out too. :confused: 

I could show you the error from the deb if you would like? 

AJ:rolleyes:

---

### Post by oedha on 2008-01-30
i search about this handbrake......i am not sure abou it
why dont you use dvdrip ?
have you follow all step from [http://ubuntuforums.org/showthread.php?t=571637](http://ubuntuforums.org/showthread.php?t=571637)
#9 ??
-Download linux binary from Handbrake site    <----- get this (1)
-Extract then copy HandBrakeCLI to /usr/bin    <------ extract and put the HandBrakeCLI to /usr/bin
-Download HandBrakeGTK from here [http://sourceforge.net/projects/handbrakegtk](http://sourceforge.net/projects/handbrakegtk)  <--- get this (2) -- when i checked...it's invalid project 
-extract, goto extracted directory, goto bin directory, copy HandBrake directory to /home/username/.config  <--- extract and find bin folder , open it...take HandBrake folder to .config
-chmod 0755 HandBrakeGTK.exe   <--- find this *.exe file and then sudo chmod 755 ~/HandBrakeGTK.exe
-copy the HandBrakeGTK.exe to where ever you want to run it from
-sudo apt-get install mono
-sudo apt-get install mono-devel
-sudo apt-get install gtk-sharp
-run 'mono ./HandBrakeGTK.exe' to start the gui  <--- maybe if you put hadbrak.exe on desktop...it become 'mono /home/jay/Desktop/HandBrakeGTK.exe

~E~

---

### Post by ajgoyt on 2008-01-30
E and everyone thanks for your help - I relaxed a bit then tried to install the DEB file again after carefully reading the error i found out it was another application that borking the install of Handbrake - I removed that application and Wallah - Handbrake installed successfully, So now comes the real test will it actually encode videos for me in x264 format.

Cheers:lolflag:

AJ:guitar:

---

