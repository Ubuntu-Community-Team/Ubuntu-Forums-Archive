---
title: "Installing StarOffice or .rpm"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2006-10-31
I having problems installing StarOffice (I get it free). I've downloaded it from the website onto my Desktop.

The file is called:

so-8-pp3-bin-linux-en-US-sh

I believe it's a .rpm file (on the StarOffice website there was only a 'Linux' version). But in properties it's also called a shell script. 

Could someone walk me through so I also know how to install other .rpm files.  I'm reasonably comfortable using terminal. And I've installed Alien so I can handle .rpm files.

I know there's another thread on installing StarOffice but it didn't work.

Thanks

Tweed.

I'm using Edgy.

---

### Post by tronica on 2006-10-31
ok pretty simple. from the command line. cd to the directory in which it is, so lets say its in your home.

> cd /home/you

then run this command to launch it.

> ./so-8-pp3-bin-linux-en-US-sh

that should launch it.

---

### Post by Tweedicus on 2006-10-31
Ok. I did the following:

cd /home/ahmedweir/Desktop

because that's where the file is, all 170mb of it, I can see it so I know it's there, and I right clicked and selected properties and copied the location.

Then I got:

ahmedweir@ahmedweir-laptop:~/Desktop$ 

So I then typed:

./so-8-pp3-bin-linux-en-US-sh

And I got:

bash: ./so-8-pp3-bin-linux-en-US-sh: No such file or directory
ahmedweir@ahmedweir-laptop:~/Desktop$ 

Any thoughts?

Tweed

---

### Post by Tweedicus on 2006-10-31
I also get this if I try to use alien, which I thought I had to, because I thought I had to because StarOffice was an .rpm. 

ahmedweir@ahmedweir-laptop:~/Desktop$ sudo alien -k so-8-pp3-bin-linux-en-US.sh 
Unknown type of package, so-8-pp3-bin-linux-en-US.sh.

---

### Post by disc on 2006-10-31
Try this:

First, open the terminal and run as root,

sudo -i

Then, switch to your desktop directory,

cd /home/ahmedweir/Desktop

Then, run the command to convert to .deb using alien,

alien -d o-8-pp3-bin-linux-en-US-sh.rpm

Wait a few seconds, then it should say the conversion was successful.

---

### Post by Tweedicus on 2006-10-31
OK did exactly what you said, and all went well until the final command. Here's what I got:

ahmedweir@ahmedweir-laptop:~$ sudo -i
Password:
root@ahmedweir-laptop:~# cd /home/ahmedweir/Desktop
root@ahmedweir-laptop:/home/ahmedweir/Desktop# alien -d o-8-pp3-bin-linux-en-US-sh.rpm
File "o-8-pp3-bin-linux-en-US-sh.rpm" not found.
root@ahmedweir-laptop:/home/ahmedweir/Desktop#

I did read that the StarOffice sh file is an installer script. Does this shed any light?

---

### Post by disc on 2006-10-31
Try "sh ./so-8-pp3-bin-linux-en-US.sh" as the last command.

---

### Post by tronica on 2006-10-31
where is the file located?

---

### Post by Tweedicus on 2006-10-31
OK we're getting somewhere.

I'm getting this:

root@ahmedweir-laptop:/home/ahmedweir/Desktop# sh ./so-8-pp3-bin-linux-en-US.sh

Select the directory in which to save the unpacked files. [/var/tmp/unpack_staroffice] 

I have a flashing cursor, what do I type? Where do I unpack to, and what do I do after?

---

### Post by fazavon on 2006-10-31
First sud -i 
ok if it is a something.sh you need to change it to an executable 
so navigate to the dir (directory) in which it resides 
 then just run

chmod +x whatever.sh

then 

./whatever.sh

---

### Post by Tweedicus on 2006-10-31
I tried that too and it's as above:

I'm getting this:

root@ahmedweir-laptop:/home/ahmedweir/Desktop# sh ./so-8-pp3-bin-linux-en-US.sh

Select the directory in which to save the unpacked files. [/var/tmp/unpack_staroffice]

I have a flashing cursor, what do I type? Where do I unpack to, and what do I do after?
Edit/Delete Message

---

### Post by tronica on 2006-10-31
i would just put it in your home directory, just give it the path to your home directory.

---

### Post by Tweedicus on 2006-10-31
This is what I get when I enter the command after it asks me where to unpoack to, I tried various things as you can see:

/home/ahmedweir/Desktop
Directory /home/ahmedweir/Desktop already exists.
Please select a new directory name.
root@ahmedweir-laptop:/home/ahmedweir/Desktop# /home/ahmedweir
-bash: /home/ahmedweir: is a directory

root@ahmedweir-laptop:/home/ahmedweir/Desktop# /home
-bash: /home: is a directory
root@ahmedweir-laptop:/home/ahmedweir/Desktop#

---

### Post by disc on 2006-10-31
Redo the "sh ./so-8-pp3-bin-linux-en-US.sh" command, then when it asks for a directory, try naming a directory that doesn't exist, for example "/home/ahmedweir/Staroffice"

---

### Post by Tweedicus on 2006-10-31
Thanks disc. That last thing did the trick. It's installed, up and running. I might write a quick guide now for installation for beginner based on these posts. By the way, it sucks on Ubuntu. On Windows Staroffice is better than Oo, on Ubuntu, Oo displays the fonts much better.

---

