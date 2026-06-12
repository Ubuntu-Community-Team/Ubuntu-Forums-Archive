---
title: "Nautilus will not start up"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Hookheathen on 2008-03-11
Calamity of calamities.

Nautilus would not function to get me to my file browser. I wished to reinstall Nautilus and removed Nautilus using Synaptic then planned to reinstall. However it appears I did not reinstall it completely and I am unable to run Ubuntu Fiesty. In recovery mode it checks files but leaves me at root. I have tried the command to install nautilus but I am advised I am missing some files, what commands do I need to get missing files or total reinstall of Nautilus?

Thanks for any guidance.

---

### Post by drdrewdown on 2008-03-11
just remove all the files inside /home/user/.nautilus

---

### Post by Hookheathen on 2008-03-11
> **drdrewdown said:**
> just remove all the files inside /home/user/.nautilus

How is this done? I cannot get as far as accessing any files. If I boot up normally I just get a blank coffee coloured screen and a cursor, nothing else. Do you suggest booting up in recovery mode, then what instructions to I use when it stops at the line notifying I have missing files and the root command?

---

### Post by drdrewdown on 2008-03-11
can you be more specific as to the error msg you're gettin?

instead of removing nautilus you could have just blown everything out of that directory & been ok

if you can boot in console mode, try cd /home/user/.nautilus & then rm *

---

### Post by Hookheathen on 2008-03-11
Is there a console mode on the boot menu? To communicate and function I am using the Windlows side of my dual boot.

---

### Post by Hookheathen on 2008-03-11
> **Hookheathen said:**
> Is there a console mode on the boot menu? To communicate and function I am using the Windlows side of my dual boot.

Please put my stupid question down to jetlag.

In recovery mode terminal inserted "cd /home/user/.nautilus and got "no such file or directory".

So it appears i have lost more files than thought. What can I do now? I am currently travelling in China and do not have any start up CD.

---

### Post by DaV|d on 2008-03-11
Try reinstalling nautilus:
```
sudo apt-get install --reinstall nautilus
```

---

### Post by Hookheathen on 2008-03-11
Thanks will give it a shot and get back to you.

---

### Post by Hookheathen on 2008-03-11
> **DaV|d said:**
> Try reinstalling nautilus:
```
sudo apt-get install --reinstall nautilus
```

This is the resulting  msg I get:-

"Package nautilus is not availiable, but is supported by another package..........missing, or has been obsoleted or only available from another source
libgnome2-common

E: Package nautilus has no installation candidate."

So I guess I need to access this file, how to go about that?:confused:

---

### Post by Hookheathen on 2008-03-12
[COLOR="DarkRed"]Help I'm getting nowhere here[/COLOR]....

In recovery mode tried
cd/home/michael/.nautilus and then rm*
output was:
bash:rm*: command not found.

Any suggestions?

---

### Post by drdrewdown on 2008-03-12
rm* is not a command
you need a space in between rm & *


```
rm *
```

---

### Post by DaV|d on 2008-03-12
> **Hookheathen said:**
> This is the resulting  msg I get:-

"Package nautilus is not availiable, but is supported by another package..........missing, or has been obsoleted or only available from another source
libgnome2-common

E: Package nautilus has no installation candidate."

it seems that your sources.list file has been changed or corrupted.

Try the following in a terminal (no need to copy the code after the '#'): 
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak #make a backup just in case
sudo su #to get a root terminal. Enter your password when prompted
echo "deb http://archive.ubuntu.com/ubuntu/ feisty main" >> /etc/apt/sources.list #adds the feisty repositories to your sources.list file
apt-get update #Reloads the repository contents
apt-get install --reinstall nautilus #if everything went well, reinstalls nautilus

```

Keep us posted of your progress, and good luck! :)

---

### Post by Hookheathen on 2008-03-12
> **drdrewdown said:**
> rm* is not a command
you need a space in between rm & *


```
rm *
```

OK amended code to rm * as you suggested but got output "cannot remove metafiles it is a directory".

OTU

---

### Post by Hookheathen on 2008-03-12
> **DaV|d said:**
> it seems that your sources.list file has been changed or corrupted.

Try the following in a terminal (no need to copy the code after the '#'): 
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak #make a backup just in case
sudo su #to get a root terminal. Enter your password when prompted
echo "deb http://archive.ubuntu.com/ubuntu/ feisty main" >> /etc/apt/sources.list #adds the feisty repositories to your sources.list file
apt-get update #Reloads the repository contents
apt-get install --reinstall nautilus #if everything went well, reinstalls nautilus

```

Keep us posted of your progress, and good luck! :)

Input as instructed but got a familiar output
"Package Nautilus is not available.....by another package........missing or has been obsoleted or only available from another source
libgnome2-common
E:package Nautilus has no installation candidate"

What do you suggest now?

---

### Post by drdrewdown on 2008-03-13
this is an idea i had that may need more input from others, but what if you removed ubuntu-desktop

```
sudo apt-get remove ubuntu-desktop
```

& then re-install it

```
sudo apt-get install ubuntu-desktop
```
nautilus is the file manager in gnome so in theory this would remove everything & put it back.

like i said this is a theory that may or may not be the proper way to do things...

input from others would be helpful

---

