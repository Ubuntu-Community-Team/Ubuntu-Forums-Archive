---
title: "ssh removal"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mrphud on 2008-01-03
Hi

I recently tried to setup a ssh by entering "ssh hpc.usc.edu" (without the quotes). 

The only problem is it automatically signed me in with the wrong user name. I also noticed that it 'permantly' added the hpc.usc.edu, 128.#### to a RSA list.

What I would like to do is to undo or remove what was added. I noticed in places that there was a much easier way to connect to another server. Please, any help would be appreciated.

Thank you

---

### Post by p_quarles on 2008-01-03
The best way to connect to an ssh server is to use this syntax:
```
ssh username@server.url
```
If you're just trying to get rid of the entry that this initial connection made on your system, you can open your file manager, click on "show hidden files," go into the folder marked .ssh, and delete the file called "known_hosts."

---

### Post by kestrel1 on 2008-01-03
You could always try Putty.
This is an ssh client with a gui interface. To install it try this:
```
sudo apt-get install putty
```

---

### Post by mrphud on 2008-01-03
Ok I see what you are saying but I am having trouble navigating the system. I cant find file manager nor can I find .ssh. I don't know where to look. I started using 7.10 last night. If you could be a little more explicit I would appreciate it.

---

### Post by p_quarles on 2008-01-03
> **mrphud said:**
> Ok I see what you are saying but I am having trouble navigating the system. I cant find file manager nor can I find .ssh. I don't know where to look. I started using 7.10 last night. If you could be a little more explicit I would appreciate it.
Sure thing. Go to the "Places" menu on the top panel, and click on "Home." This will bring up the file manager. To display hidden files, you can either hit ctrl-h, or click on "View" and select "display hidden files."

You should now be able to see the folder called .ssh.

---

### Post by mrphud on 2008-01-03
I used putty when I had windows. I thought that using linux would usurp programs like putty. Also where did you guys learn how to script? Meaning how did you learn to comprehend the bash language. I know a few basic commands but I am so used to windows point and click that I can't understand what is being said with the apt-install stuff. I am also a bit uneasy because if I make a typo I fear I will screw up the system. Any info helps.

Thanks again

---

### Post by mrphud on 2008-01-03
SWEET!!. I found it. Thank you for all the help.

---

### Post by The Cog on 2008-01-03
I have a dirty secret. I've been using Linux for several years, and I still don't understand the bash "language". That command **sudo apt-get install putty** is nothing to do with bash at all. 

Sudo is a program that does the following command as the administrator (SuperUser DO ...). This is for when you wnat to do things that a normal user isn't allowed to, such as installing software.

apt-get is the software installing program. It can instal (and remove) software packages. In this case we want to tell it to install a package, called putty. 

So all together we have a command that says that as superuser we want apt-get to install putty. Most of the commands you see posted here are like that. They are not "code" as such, just the name of a program followed by some words that the program understands telling it what to do. Another example is **rm /etc/fstab** which will try to remove (a program called rm) a rather vital file called /etc/fstab - this will fail with a permission denied - **don't** do it with sudo or you will have to reinstall.

The one bash thing that I did learn early on is that you can pass the output of one command into another, chaining a series of command/programs together to produce a complex result. This is a concept totally alien to GUI users, but is very powerful for those who take the time to get to understand it. As an example, the command:
**df -h | grep home**
will list the free disk space (df) on each partition of the hard disk and pass this list to grep which will search for and only output lines containing the word "home". I was rather proud of this one a few weeks ago:
**grep '|' xxx | sed 's:| *::' | sed 's: *|$':: | sed 's: *| *:,:g' > yyy**
which took a 25 megabyte file that looked like this:
[b]+------+--------+
| Name | Number |
+------+--------+
| Andy | 1234   |
| Bill | 234    |
+------+--------+[/b]
and created one that looked like this:
[b]Name,Number
Andy,1234
Bill,234[/b]
but that line took me quite a while to work out, and only used two commands - grep and sed. Still, with a GUI editor, it just would not have been possible because of the file size, I think.

But back to the plot. Most things people post commands for can be done with a GUI, but it's quicker and easier to give someone the command than to write an essay on what to find, click, click, click to do the same thing.

---

