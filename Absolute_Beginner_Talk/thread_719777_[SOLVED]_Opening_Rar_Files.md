---
title: "[SOLVED] Opening Rar Files"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by imanoob on 2008-03-09
Hey I really need help opening a .rar file. I've tried installing unrar-free through Synaptic but  I can't locate it. Please help me.

---

### Post by halitech on 2008-03-09
in synpatic do a search for rar and it shoudl find it. you will need to enable to extra repos as well though

---

### Post by imanoob on 2008-03-09
I have found and have installed it, but I'm unsure how to use/run/find it.

---

### Post by halitech on 2008-03-09
use Nautilus to locate the file then just right click extract here

---

### Post by imanoob on 2008-03-09
Where can I find Nautilus? Sorry I'm a real noob at Ubuntu.

---

### Post by halitech on 2008-03-09
Places - Home will open it for you

---

### Post by imanoob on 2008-03-09
All I get when I right click it is:
```
Open with "Archive Manager"
Open with File Browser
Open with Other Aplication
Cut
Copy
Make Link
Rename
Move to trash
Extract here <-- Gives me an error
Send to...
Properties
```

---

### Post by halitech on 2008-03-09
what is the error you get when you use Extract here?

---

### Post by imanoob on 2008-03-09
Could not open filename.rar
Archive type not supported.

---

### Post by halitech on 2008-03-09
ok, so the file you want is not supported by unrar. you could try installing 7zip, the unfree unrar and rar, hopefully one of them could do it.

---

### Post by imanoob on 2008-03-09
How do I install the "unfree rar" from rarlabs?

---

### Post by halitech on 2008-03-09
I'm not sure, I've never had to install it

---

### Post by imanoob on 2008-03-09
Well thanks anyways. How do you open rar files then?

---

### Post by halitech on 2008-03-09
I installed rar and 7zip from the repos and then just right click extract here and it works for me

---

### Post by Ardrias on 2008-03-09
You will need to enable the multiverse repository. After that unrar should be available through Synaptic.

---

### Post by prshah on 2008-03-09
> **imanoob said:**
> Well thanks anyways. How do you open rar files then?

Open Applications-Accessories-Terminal.

to extract files use the command;

```

~$ mkdir unrard && unrar ex filename.rar ./unrard/

```

for more information, type the below in a terminal:

```

~$ man unrar

```

Cheers,
PRShah

---

### Post by imanoob on 2008-03-09
How do I enable multiverse repositories?

---

### Post by imanoob on 2008-03-09
Help anyone? Please.

---

### Post by halitech on 2008-03-09
System - Administration - software sources

make sure the top 4 items are checked

---

### Post by mali2297 on 2008-03-09
> **imanoob said:**
> Help anyone? Please.

See [here]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096").

---

### Post by prshah on 2008-03-10
> **imanoob said:**
> How do I enable multiverse repositories?

unrar (command-line) comes already installed with the system.  You dont need to install anything.

Just open the Terminal and type "man unrar" to show the help pages for unrar, or follow the commands I've given earlier.

Cheers,
PRShah

---

### Post by imanoob on 2008-03-10
```
ubuntu@ubuntu:~$ man unrar
No manual entry for unrar
ubuntu@ubuntu:~$ unrar
The program 'unrar' is currently not installed.  You can install it by typing:
sudo apt-get install unrar
bash: unrar: command not found
```

---

### Post by stchman on 2008-03-10
> **imanoob said:**
> Hey I really need help opening a .rar file. I've tried installing unrar-free through Synaptic but  I can't locate it. Please help me.

If you do the following:

```
sudo apt-get install rar unrar
```

This will allow Archive manager to pack and unpack .rar files.  After package installation you can double click on the .rar archive and you are good to go.

---

### Post by imanoob on 2008-03-10
```
ubuntu@ubuntu:~$ sudo apt-get install rar unrar
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$
```

---

### Post by AndyCooll on 2008-03-10
You haven't got Synaptic open at the same time have you?

Otherwise: 
```
sudo rm /var/lib/dpkg/lock
```
Followed by:
```
sudo dpkg --configure -a
```

:cool:

---

### Post by imanoob on 2008-03-10
lol
```
ubuntu@ubuntu:~$ sudo apt-get install rar unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
```

---

### Post by FuturePilot on 2008-03-10
Do you have all of the repositories enabled?

---

### Post by AndyCooll on 2008-03-10
> **imanoob said:**
> lol
```
ubuntu@ubuntu:~$ sudo apt-get install rar unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
```
Since you are only wanting to extract the file, I'd just start off by installing unrar.

And by all repositories he means also "multiverse" which is where the rar package is.

:cool:

---

### Post by imanoob on 2008-03-10
So wait, how do I go about installing it and not extracting it. If this helps: I'm on a live cd.

---

### Post by Corvair on 2008-03-10
Halitech,

Thanks for the information. I was looking for a way to open rar files and you 
did it for me. I installed both rar and 7zip from synaptic and now I can extract rar files

---

### Post by imanoob on 2008-03-10
What the ****! Why is it so hard for me. :(

---

### Post by Corvair on 2008-03-10
You probably are missing some repositories.
Follow the instructions oyu were given to install extra repositories and reload once they are installed and you should be able to see rar and 7zip when you do a search.

---

### Post by imanoob on 2008-03-10
I installed 7zip and unrar.

---

### Post by imanoob on 2008-03-10
I guess this is un-explanable?

---

### Post by chris200x9 on 2008-03-10
you have 7zip right? system>administration>synaptic package manager

search for rar install...... then it double click the rar it should open archive manager hit extract and select a destination.


assuming you have 7zip.....this is all i did :)

---

### Post by imanoob on 2008-03-11
I really don't get why it's not working. I have installed 7zip but I cannot find it! Is there a way to refresh the os without closing it? I'm on a live cd.

---

### Post by mali2297 on 2008-03-11
Have you tried different rar files? Same result?

---

### Post by FuturePilot on 2008-03-11
p7zip is a command line utility. However the Archive manager can create and extract 7z archives with it installed. Try double clicking on a 7z archive, it should open.

---

### Post by imanoob on 2008-03-11
So I should just make an un-named file and name it to let's say file.7z?

---

### Post by imanoob on 2008-03-11
Can someone please upload a 7z file please. I can't find one :P!

---

### Post by imanoob on 2008-03-11
Never mind, I made one.

---

### Post by halitech on 2008-03-11
> **Corvair said:**
> Halitech,

Thanks for the information. I was looking for a way to open rar files and you 
did it for me. I installed both rar and 7zip from synaptic and now I can extract rar files

glad it worked for someone :)

---

### Post by imanoob on 2008-03-12
I did it! I finally did it! I somehow found the unfree version, I installed it and it ran fine. I have no idea how I found it but well thanks for all your help guys.

---

