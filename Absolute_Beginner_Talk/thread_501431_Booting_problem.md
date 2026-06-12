---
title: "Booting problem"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by IAmALinuxFool on 2007-07-15
Hi all,

I was having a few problems with the keyring manager so i read up on it and installed libpam and edited the gdm file so it would auto login or whatever it does, but then i had a 'failed authentication' box pop up every 2-3 seconds, which made it impossible to do anything. So i rebooted in to recovery mode, and (foolishly now i realise) deleted the gdm file, that didnt work so i deleted the rest of the pam directory. Now every time i boot up , X doesnt start, but a window saying something along the lines of 'could not read pams configuration for GDM' and goes to the command line. Is there any way i can fix this please? 

Thanks,

Dan.

---

### Post by davidjmayo on 2007-07-15
Look in trash

Copy back the files if they are still there

---

### Post by starsky on 2007-07-15
hi there :)

it seems the pam configuration is missing bceause gdm reads it during login and obviously you said you deleted it. :)

I suggest you do is reinstall pam runtime module

Type what is shown below exactly without the "$" after you get into the shell prompt (you said it drops you to a command line. type these there).

```

$ sudo apt-get install libpam-runtime

```
only if you deleted the /usr/share/pam directory
otherwise post back and i'll see what i can do. :)

HTH

---

### Post by starsky on 2007-07-15
forgot to mention - make sure you do this after libpam-runtime is install

```

$ sudo invoke-rc.d gdm restart

```

HTH

---

### Post by IAmALinuxFool on 2007-07-15
Thanks for the replies, 

Sorry i forgot to mention i can't boot in to any GUI, it's just the command line. I'm using my vista partition to write on here :(

---

### Post by starsky on 2007-07-15
> **IAmALinuxFool said:**
> Thanks for the replies, 

Sorry i forgot to mention i can't boot in to any GUI, it's just the command line. I'm using my vista partition to write on here :(

read the post above :) 
I edited it after reading that "command line" sentence

---

### Post by IAmALinuxFool on 2007-07-15
I just did the above, and i get the msg 'libpam-runtime is already the newest version'...

---

### Post by starsky on 2007-07-15
> **IAmALinuxFool said:**
> Hi all,

I was having a few problems with the keyring manager so i read up on it and installed libpam and edited the gdm file so it would auto login or whatever it does, but then i had a 'failed authentication' box pop up every 2-3 seconds, which made it impossible to do anything. So i rebooted in to recovery mode, and (foolishly now i realise) deleted the gdm file, that didnt work so i deleted the rest of the pam directory. Now every time i boot up , X doesnt start, but a window saying something along the lines of 'could not read pams configuration for GDM' and goes to the command line. Is there any way i can fix this please? 

Thanks,

Dan.

what did you delete ? You said you deleted pam directory which makes me think that it's /usr/share/pam/ ? 

Please cut/paste the output of this command
```

$ sudo dpkg --list | grep pam

```

---

### Post by IAmALinuxFool on 2007-07-15
I deleted the contents of the pam directory from /etc/pam.d/ not usr... Also i cant copy and paste the output of the command because i'm having to boot between operating systems, but the output was said something about 'not being able to initialise pam'

---

### Post by starsky on 2007-07-15
hi there:)
do this

```

sudo apt-get -o DPkg::Options::="--force-confmiss" --reinstall install libpam-runtime 

```

post back. :)

---

### Post by IAmALinuxFool on 2007-07-15
Hi,

I just tried that and i got this:

Sudo: Unable to initialize pam: No such file or directory

Will i be connected to the net (wireless or otherwise) from command line? i ask because of the apt-get command. Also is there a config file or something i can edit so ubuntu just doesnt look for pam when it starts up? Thanks for your continued help...

Dan.

---

### Post by IAmALinuxFool on 2007-07-16
bump

---

### Post by starsky on 2007-07-16
hi there :)
that command i gave you earlier reinstall libpam-runtime which btw creates the /etc/pam.d/ folder.

Since, you deleted the /etc/pam.d directory, apt-get assumes that you deleted that folder on purpose (and apt-get install libpam-runtime won't RECREATE it for you) unless you pass the option --force-confmiss to dpkg (dpkg works for apt-get).

if that didn't work then sorry i can't help you because as far as i know, /etc/pam.d is created by libpam-runtime and since if that doesn't reinstall all the configuration files in /etc/pam.d to default, i don't see any other method of installing it except for maybe copy that from your friend or something.

HTH

---

### Post by starsky on 2007-07-16
> **IAmALinuxFool said:**
> Hi,

I just tried that and i got this:

Sudo: Unable to initialize pam: No such file or directory

Will i be connected to the net (wireless or otherwise) from command line? i ask because of the apt-get command. Also is there a config file or something i can edit so ubuntu just doesnt look for pam when it starts up? Thanks for your continued help...

Dan.

I don't think you can do that because gdm is hard coded AFAIK to depend on PAM (pluggable authentication module). But if you can get IP address from your router's dhcp server, that generally means you can use internet.
If the apt-get is failing to connect to internet, it obviously means you can't connect to internet :)

HTH

---

### Post by IAmALinuxFool on 2007-07-16
I think a fresh install is the way to go, thanks for all your help though, it was much appreciated.

Dan.

---

