---
title: "wireless internet conection"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by mulleta on 2006-12-24
Hi,

i am new to ubuntu dapper and also new to connecting to the internet wirelessly. could someone explain what to do? that would be greatly appreciated.

Also i would like to install certain packages like gcc etc. where could i do this. I know how to use suse's YAST control system. is there a similar application in ubuntu dapper?

much appreciated, thanks

andrew

---

### Post by Mazen on 2006-12-24
Hello,
Well welcome to Ubuntu world!:)
To install stuff such as gcc
just open a terminal and go : ```
sudo apt-get install gcc
```
 or you can use Synaptic which is a package manager in Ubuntu go System > Administration > Synaptic Package Manager and just search for what you would like to install

As for how to connect to a wireless internet network u can install software such as WiFi-Radar try searching it in Synaptic too 
hope that helped.

-Mazen

---

### Post by mulleta on 2006-12-24
thank you for your help, am attempting it now!

---

### Post by spockrock on 2006-12-24
for wifi you can use wifi radar, or network-manager-gnome.

like the previous poster mentioned you can use apt or synaptic.  As for gcc, may I suggest you install build-essential as the will install all your compiling needs.

---

### Post by mulleta on 2006-12-24
hi, thanks for your posts.

um when executing the sudo apt-get install gcc command it finishes saying package not found.

in synaptic when i check the status of say, gcc base 4.0 then it says installed, yet when i try activate the compiler in a shell/terminal then it says unknown command?

when in synaptic i cant seem to install any packages...it doesnt give me the option to add the packages...only to remove them, but that doesnt seem right as there are so many available packages and im pretty sure that not all of them are intalled?

thanks again

---

### Post by Mazen on 2006-12-24
are you connected to the internet? because Synaptic or the "apt" command will go and fetch the packages from the net

---

### Post by mulleta on 2006-12-24
no i am not. i am switching between linux and windows on the same laptop.

when in ubuntu i am unable to coonect and so want to see if i can use a wifi app to pickup the wireless network.

---

### Post by Mazen on 2006-12-24
well connect urself to some wired  internet for the moment so that you could install the packages...

---

