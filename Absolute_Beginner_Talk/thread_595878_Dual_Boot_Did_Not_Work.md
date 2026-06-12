---
title: "Dual Boot Did Not Work"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by gperk on 2007-10-29
Hello,
I installed edubuntu 7.10 on a XP machine, wanting to keep XP with dual boot possibility. When I did the instalation, the instructions said I would be able to do this, that a boot menu would appear at start up. 
This does not happen - edubuntu just boots. 
When I look at the partition info (in dos fdisk - booted from a floopy) I see that 
partition 1 is still NTFS,
2 is Ext Dos
and 3 is A, Non - Dos. 
Is there anything I can do now to get grub to give me the dual boot thing?
Also, I wonder where the scratch disk partition is which should have been created when the install was done. 
Thanks very much. 
Greg

---

### Post by skymera on 2007-10-29
edubuntu? whats it for? schooling?

try

sudo update-grub

gksudo gedit /boot/grub/menu.list

to see if windows is thar

---

### Post by gperk on 2007-10-29
Thanks for the response,
I have installed edubuntu server for a school, the main reason is to put in a web filter. Please see my other post, below, which no one has replied to yet. 

"update -grub" worked OK but with 
"gksudo gedit /boot/grub/menu.list" I only got command not found. I also tried sudo gedit... with the same result
___________________________________________
I am intending to use edubuntu as a plain server for a school, to start there will be 5 to 10 computers connected, no thin clients. I just installed the latest server version, 7.10.
I mainly want to create a web filter to protect against the students accessing adult content.
Can anyone tell me how to do this or where I can find instructions?

Also, it seems that something went wrong during installation withinstalling all the software, this does not matter so much but when it boots I only get a command prompt. I can login and commands work but it looks just the same as Ubuntu server. Is this normal?

Thanks thanks thanks for replying...
Greg

---

### Post by skymera on 2007-10-29
ok swap gedit for nano :D

---

### Post by constrictor on 2007-10-29
i think the command should be gksudo "gedit /boot/grub/menu.list"

---

### Post by skymera on 2007-10-29
he sais gedit wasnt recognised

gksudo nano /boot/grub/menu.list

---

### Post by gperk on 2007-10-29
I get:
-bash: gksudo: command not found
sudo: nano: command not found
sudo: gedit: command not found

---

### Post by skymera on 2007-10-29
right ok.

now im confused :confused:

but can you boot into windows now?

---

### Post by so7777777os on 2007-10-29
> **gperk said:**
> Hello,
I installed edubuntu 7.10 on a XP machine, wanting to keep XP with dual boot possibility. When I did the instalation, the instructions said I would be able to do this, that a boot menu would appear at start up. 
This does not happen - edubuntu just boots. 
When I look at the partition info (in dos fdisk - booted from a floopy) I see that 
partition 1 is still NTFS,
2 is Ext Dos
and 3 is A, Non - Dos. 
Is there anything I can do now to get grub to give me the dual boot thing?
Also, I wonder where the scratch disk partition is which should have been created when the install was done. 
Thanks very much. 
Greg

I'm a new Ubuntu user....and i try to know what's you said ,haha...in a word....i can't help you....

---

### Post by coffeecat on 2007-10-29
Let me have a go here. :)

> **skymera said:**
> gksudo nano /boot/grub/menu.list

won't work because nano is not a gtk (GUI) app. It's a very basic, but very good, text editor to be used from the terminal.

**gperk**, I have no experience of the edubuntu version of Ubuntu, but I'm wondering if menu.lst has in fact been set up for a dual-boot but that the 'hiddenmenu' option has been enabled for some reason.

OK. From a terminal, try:

```
sudo nano -w /boot/grub/menu.lst
```If you have nano installed this will open nano in the terminal. The -w option is to stop it word-wrapping and putting in carriage returns where you don't want them. If this works, look for two lines. The first might be:

```
hiddenmenu
```If that appears without a hash mark (#) at the beginning of the line, then the grub menu is being suppressed at bootup. All you need do is put in a hash mark as the first character of that line, like this:

```
#hiddenmenu
```The second thing to look for is a line starting with 'timeout'. If you can find such a line (again with no hash mark at the beginning) the number that follows 'timeout' is the number of seconds before grub boots the default OS. If you have something ridiculous (less than 5), change the line to read:

```
timeout 10
```or 20 or 30 or however long you want the menu to stay on screen.

If, by chance, you cannot get nano to work, do one of two things. Try:

```
sudo pico -w /boot/grub/menu.lst
```or look in your package manager to see whether nano is installed. If not, install it. :wink:

**Edit:** I've just had a look at the Edubuntu home page, and I see that Edubuntu uses Gnome as the Desktop Manager. This means that if gedit is not installed as default (which I doubt), then gedit will work fine if you install it. Just to be sure you've tried to start gedit correctly, did you try this command, exactly as I have typed it in the code box?

```
gksudo gedit /boot/grub/menu.lst
```If that doesn't work then have a look for gedit in your package manager, install it and try again.

The advantage of gedit over nano is that it is a GUI text editor. I think previous posters have suggested looking in menu.lst so that you can see what is in it. If you manage to open it with gedit, use copy and paste to post the contents here, and then everyone can help.

---

### Post by Prometheum on 2007-10-29
To make some things clear:

1.) Are you using Edubuntu Desktop or Server? From the role of the machine it looks like you'd be using Server, which to my knowledge doesn't have a GUI. So that's why you don't have a gui and why you can't gksudo or gedit.

2.) Most likely, hiddenmenu is enabled. If you want XP to be the default boot option, move its entry above that of Edubuntu's in menu.lst.

---

### Post by gperk on 2007-10-29
OK,
Thanks for the replys.
I am using edubuntu server. The screen shots on the edubuntu instructions page show a GUI so that is why I thought there should be one. 
I managed to install probably the rest of edubuntu and now I get the GUI. But when I rebooted there was still no boot manager, it just booted straight into edubuntu. 
Anyway, I did the sudo update-grub thing seemed to work fine, and then gksudo gedit/boot... and it opened menu.list in a gedit window but that document has no text at all in it. 
I don't want XP to be the default right now, I just want to have the boot options. 
Thanks

---

### Post by gdoutch on 2007-10-30
I recently had a similar sort of problem. If you can go into GParted on the live CD to check your drive naming convention and make sure that the drive that is booted into is called '/'

See the thread:
[Error loading operating system]("http://ubuntuforums.org/showthread.php?t=592584")

---

### Post by Prometheum on 2007-10-30
The above poster's problem seems to have nothing to do with this.

Make sure you're editing the right file. it should be "/boot/grub/menu.lst". If you run nano/gedit with a file that doesn't yet exist, it'll create one for you, hence the empty file. You most definitely have a menu.lst file on your system if you're using grub, so just make sure you type it in right.

---

