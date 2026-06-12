---
title: "using terminal to move ttf files"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Starry on 2007-02-16
ok i finally figured out where all my font files are on my hard drive.

/usr/share/fonts/truetype

i have all these ttf font files unzipped/usr/share/fonts/truetype that i want to move from my home folder TO that folder but i am kind of at a loss at how to do that.  i tried to do it on my own and did a little googling to get the right bit of code to do it but its all greek to me. [same as getting flash 9 installed still, i just went away for a week instead]

i think i know where my first issue is: in terminal i am not in the right place to start from; ie the home folder where i want to move the files from.  so i need to learn how to get there first.  then i am pretty sure i need to put in

#sudo 1942.ttf cp /usr/share/fonts/truetype 

to get the ttf file to move where i want it to right?  [1942.ttf is one of the fonts i have to move as an example, please use it to keep me straight as this is ALL new to me pretty much]

i am not the root user on my laptop but i know the password and i can work as the root user if need be.  if it would be better to do things as such TELL me.  assume i am dumb as a stick.

thanks kindly!!!

---

### Post by taurus on 2007-02-16
```
sudo cp 1942.ttf /usr/share/fonts/truetype
```
Otherwise, use nautilus and drag 'n drop.

```
gksudo nautilus
```

---

### Post by highneko on 2007-02-16
Also if you're wanting the ttf files from your windows partition I wrote this tutorial:
```
[COLOR="Gray"]# First make the hidden folder named ".fonts" in the home directory:[/COLOR]
mkdir ~/.fonts
[COLOR="Gray"]# Copy the files. Replace the word "Example" with the mounted folder you choose for windows:
# The location of the windows fonts may be different for you. I have a mounted vista.[/COLOR]
sudo cp /Example/Windows/Fonts/* ~/.fonts
[COLOR="Gray"]# Then maybe you should change the permissions or ownership of the moved font files:[/COLOR]
sudo chown $USER:$USER ~/.fonts/*
[COLOR="Gray"]# Then the permissions to -rw-r--r--:[/COLOR]
sudo chmod 644 ~/.fonts/*
```

---

### Post by Starry on 2007-02-16
> **taurus said:**
> ```
sudo cp 1942.ttf /usr/share/fonts/truetype
```
Otherwise, use nautilus and drag 'n drop.

```
gksudo nautilus
```

oops i did put the cp first when i tried to do this and it didn't move.  again the problem is that i am NOT in the right place in terminal.  how do i get into the home folder where all these files are?  when i was here trying to get flash 9 installed last week the last 2 files refused to move from my desktop to the right place, no matter what we did.  in the end the last thing we tried [or figured the problem was] was that i wasn't working from the right place on my laptop.

at least my sudo wasn't broken.  :)

---

### Post by taurus on 2007-02-16
Maybe all your download stuff is in Desktop.

```
cd ~/Desktop
ls -la
```
Paste the output of the second command here.

---

### Post by Starry on 2007-02-16
> **highneko said:**
> Also if you're wanting the ttf files from your windows partition I wrote this tutorial:
```
[COLOR="Gray"]# First make the hidden folder named ".fonts" in the home directory:[/COLOR]
mkdir ~/.fonts
[COLOR="Gray"]# Copy the files. Replace the word "Example" with the mounted folder you choose for windows:
# The location of the windows fonts may be different for you. I have a mounted vista.[/COLOR]
sudo cp /Example/Windows/Fonts/* ~/.fonts
[COLOR="Gray"]# Then maybe you should change the permissions or ownership of the moved font files:[/COLOR]
sudo chown $USER:$USER ~/.fonts/*
[COLOR="Gray"]# Then the permissions to -rw-r--r--:[/COLOR]
sudo chmod 644 ~/.fonts/*
```


i don't have a windows partition, this is a strictly linux machine.  thanks for thinking of it though.  this is all new waters to me so changing anything is a very BAD idea :lol:

---

### Post by Starry on 2007-02-16
> **taurus said:**
> Maybe all your download stuff is in Desktop.

```
cd ~/Desktop
ls -la
```
Paste the output of the second command here.

edited out files


the first time i did that not all that stuff came up...that makes ALOT more sense now that all that stuff came up.

---

### Post by taurus on 2007-02-16
Do you remember the name of the font that you downloaded or wanted to move?

---

### Post by Starry on 2007-02-16
they are all in my /home or personal files folder not on my desktop.  there are about 20 of them.  we can work with 1942.ttf for reference's sake though.  

the confusion lies in am i working from THERE in terminal or not?

---

### Post by taurus on 2007-02-16
```
cd 
ls -la
```

---

### Post by Starry on 2007-02-16
ok that definately brought up all the fonts and stuff that i WANT to install that are in my home directory.  so i am working  from the right place.  they just won't move using the CP command in terminal.  same as the stupid last two files of flash 9 no matter what i do.

:confused:

---

### Post by taurus on 2007-02-16
```
sudo cp **font_name** /usr/share/fonts/truetype
```

---

### Post by Starry on 2007-02-16
i tried two different ones neither moved.

i'm getting pretty close to wanting to throw my laptop here.  this is totally bizzare how nothing will move.

if g-edit is broke will nothing move?  because i think it got broken when stupid flash 9 stopped its install at the last 2 files so i may have to go back and start its install from the start again and see if that will solve the problem

---

### Post by taurus on 2007-02-16
Since you wouldn't show me the command that I asked previously, I can't give you the exact command to move your fonts to /usr/share/fonts/truetype.  And when you said it didn't move, that was the error message?

```
ls -la ~
```

---

### Post by Starry on 2007-02-16
ohh i'll show you i just thought you wouldn't want to see allll that crap.

startears@starry:~$ ls -la
total 23984
edited out

like i said its a whole whack of font files and stuff and then some.

it doesn't give me an error at all.  the command goes all through just doesn't move anything.   that cholo- cherry font hasn't moved since last year.  it refused when i had someone with alot of linux knowledge trying to move the damned thing but i think it might be a screwed up font file.

---

### Post by taurus on 2007-02-16
```
sudo mv *.ttf  /usr/share/fonts/truetype
ls -la /usr/share/fonts/truetype
```

---

### Post by Starry on 2007-02-16
it kept asking me for the password and somehow i got it wrong??  i don't know so i just re-booted but i put that in and it says this now:

startears@starry:~$ ls -la /usr/share/fonts/truetype

---

### Post by taurus on 2007-02-16
The password is the same one that you use to log into your account.  Now, when you type it, you won't see any echo on the screen and that is normal (the cursor doesn't even move).  Just make sure you type the right one and hit the return key when you're done.

---

### Post by Starry on 2007-02-16
> **taurus said:**
> The password is the same one that you use to log into your account.  Now, when you type it, you won't see any echo on the screen and that is normal (the cursor doesn't even move).  Just make sure you type the right one and hit the return key when you're done.

no i don't think so, there is a root password and there is my user password.  i think i locked it because i put it in 3 times and it just keeps saying sorry.  that is one of the problems of the curser NOT moving, it'd make life easier to know if you have all the digits IN when it does.

anyways, i got this in....

startears@starry:~$ # sudo mv *.ttf  /usr/share/fonts/truetype
startears@starry:~$ ls -la /usr/share/fonts/truetype


am i just stuck now?

---

### Post by IcarusR on 2007-02-16
Hi, 
I'm also trying to add some decent fonts so I can actually do some work with Open Office.
Is it as simple as copying TTFs from Doze to /usr/share/fonts/truetype  All the current TTFs there are in their own sub directory 7 have a fonts.cash-1 file.

Sorry to but in on this thread.

---

### Post by taurus on 2007-02-16
Okay, let's get this thing over with first.  When you use sudo, you have to use the same password that you log in to your account.  NOT the root's password is there is one or if somehow you have created one.  And if it doesn't except your password, then maybe you don't belong to the right groups in /etc/group!

What's the output of this command from a terminal?

```
id
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Starry on 2007-02-16
> **IcarusR said:**
> Hi, 
I'm also trying to add some decent fonts so I can actually do some work with Open Office.
Is it as simple as copying TTFs from Doze to /usr/share/fonts/truetype  All the current TTFs there are in their own sub directory 7 have a fonts.cash-1 file.

Sorry to but in on this thread.

if you already have TTF's working its easier than not heh....other than that you need to go get some new fonts as well.  i got all mine from dafont.com, save them someplace easy to move them from and if you are the admin/root user on your system the instructions to move them to your font directory are already in here.  of course the only thing missing is the unzipping of the font, but even easier than that is to just go into the file and pull out the TTF file and move it directly to your font directory.

hope that helps.

---

### Post by Starry on 2007-02-16
> **taurus said:**
> Okay, let's get this thing over with first.  When you use sudo, you have to use the same password that you log in to your account.  NOT the root's password is there is one or if somehow you have created one.  And if it doesn't except your password, then maybe you don't belong to the right groups in /etc/group!

What's the output of this command from a terminal?

```
id
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

startears@starry:~$ id
uid=1000(startears) gid=1000(startears) groups=20(dialout),24(cdrom),25(floppy),29(audio),44(video),1000(startears)
startears@starry:~$


the reason i said that was because my ex set this laptop up for me with linux in such a way that i could NEVER screw up linux and only he could do anything to the programs/linux.  thats why i am saying that it needed the root password as i have no admin abilities.  but you'll know better than me at this point lol.

---

### Post by taurus on 2007-02-16
> **Starry said:**
> startears@starry:~$ id
uid=1000(startears) gid=1000(startears) groups=20(dialout),24(cdrom),25(floppy),29(audio),44(video),1000(startears)
startears@starry:~$


the reason i said that was because my ex set this laptop up for me with linux in such a way that i could NEVER screw up linux and only he could do anything to the programs/linux.  thats why i am saying that it needed the root password as i have no admin abilities.  but you'll know better than me at this point lol.

The reason your password doesn't work because you don't belong to groups adm & admin.  Only users belong to groups adm & admin can use sudo to install, move, or modify system files.  Therefore, you need to install the new fonts to your own $HOME/.font directory then.

```
cd
mkdir .fonts
mv *.ttf ~/.fonts
```

---

### Post by Starry on 2007-02-16
> **taurus said:**
> The reason your password doesn't work because you don't belong to groups adm & admin.  Only users belong to groups adm & admin can use sudo to install, move, or modify system files.  Therefore, you need to install the new fonts to your own $HOME/.font directory then.

```
cd
mkdir .fonts
mv *.ttf ~/.fonts
```

is this the same reason why i couldn't get flash 9 to install then?  because i was logged in as myself not root?  it would be far easier on myself to get me belonging to adm and admin....can that be done within a few steps?  or is it safe to assume that i have to be logged into my laptop as the admin first?

---

### Post by taurus on 2007-02-16
Yip.  You can't install flash to the system because you can't write to it.  However, you can still install the flash plugin to ~/.mozilla/plugins.  On the other hand, you can add yourself to groups adm and admin so you can use sudo if you wish.

Boot into recovery mode from GRUB menu and add yourself, **startears**, to groups adm (near the top) and admin (near the bottom of the file).

```
nano -B /etc/group
```
Save it with <Ctrl>x and answer the question with **Y** and Return. 

Reboot your machine with

```
shutdown -r now
```

---

### Post by Starry on 2007-02-16
do i do this recovery thing as admin or as myself?  and there are 2 recovery modes at boot.  i assume one is for admin and one is me.  there has always been the 4 options [i'm running debian 3.5 if that explains it better for you]

then after i do this i'll be able to move the font files with the sudo mv * command instead right?

---

### Post by taurus on 2007-02-16
When you boot into recovery mode (the first recovery mode on the list since it uses the lastest kernel), you are already logged in as root so just run that command at the prompt.

---

### Post by IcarusR on 2007-02-16
Hi
Sorted out my fonts. Just dumped them into fonts directory & they appear !!

Starry, hope you get yours sorted. Sorry for butting in on the thread

---

### Post by Starry on 2007-02-16
thats ok ikarus...things are SO much easier when you are the admin on your system or at least have access to do those sorts of things LOL.

taurus, ok- adm was there but there was no admin there so i went through the list and kinda just chose some stuff and put my name next to it if it made sense to me that i should have access.  if i should remove something tell me now so i can do that before i screw something up.  not in order of the list

dirmngr: x :105
debian-exim: x :102
sudo: x :27
root: x :0:

so far i tried to move the files and got permission denied.

---

