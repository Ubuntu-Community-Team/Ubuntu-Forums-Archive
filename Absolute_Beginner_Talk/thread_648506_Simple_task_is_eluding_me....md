---
title: "Simple task is eluding me..."
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by sd_smoker on 2007-12-23
I recently installed Ubuntu to dual boot with WinXP. I'd set up my /home directory in it's own partition and I'd like to also create a /data directory that will contain all my music/pictures/video that now reside in Windows. Here is what my hard drive looks like:

hda1    Windows   50Gb
hda2    /home      90Gb
hda3    /              10Gb
hda4    swap         1Gb

I had assumed that since I could access my /home directory that hda2 must be mounted, but when I ran "mkdir /dev/hda2/data" I get the following error "mkdir: cannot create directory `/dev/hda2/data': Not a directory". What am I missing here?

Also, once I'm ready to copy the files, am I anywhere in the ballpark with this command?

"cp -r /media/hda1/Documents and Settings/All Users/Documents/My Music/* /dev/hda2/data/Music/"

Thanks!

---

### Post by Moop on 2007-12-23
I'm not sure about your commands but why not just create a folder in your home directory named data? 

Trying to create a folder anywhere except /home will need to done with a sudo command.

---

### Post by wormser on 2007-12-23
> **sd_smoker said:**
> I had assumed that since I could access my /home directory that hda2 must be mounted, but when I ran "mkdir /dev/hda2/data" I get the following error "mkdir: cannot create directory `/dev/hda2/data': Not a directory". What am I missing here?
Thanks!

I have never set up /home on another drive but I believe you just need to use /home/username/data.  Test it by cd / then cd /home.  Hda2 is mounted as /home which makes Ubuntu know that it is in /dev/hda2.  Let us know if that works.

---

### Post by SOULRiDER on 2007-12-23
You dont create the directory in /dev/hda2, you create it att he mountpoint. So if hda2 is your home then what you do is
```
mkdir /home/youruser/data
                   or
mkdir ~/data
```

---

### Post by philinux on 2007-12-23
Places > Home Folder 

Right click in empty space, select create folder called data.

What could be simpler than that.

---

### Post by sd_smoker on 2007-12-23
First of all, I'm trying to do everything through the CLI in order to get familiar with it. Second, I wanted /home/data, not /home/{user}/data. Nautilus doesn't let me create a folder in /home.

I was able to create the folder. However, when I try to copy using the following command it tells me the destination directory does not exist:

cp -r "/media/hda1/Documents and Settings/All Users/Documents/My Music/*" "/home/data/Music/"

Is there an argument that tells it to create any directories that don't exist? I ran "man cp", but it wasn't clear to me if there was an option to do that.

---

### Post by philinux on 2007-12-23
If nautilus wont let you create a folder in your own home folder (not /home/user/)
something is seriously borked.

If you really need to do it from the cli it should be

```
mkdir /home/data
```

---

### Post by seventhc on 2007-12-23
> **philinux said:**
> If nautilus wont let you create a folder in your own home folder (not /home/user/)
something is seriously borked.

If you really need to do it from the cli it should be

```
sudo mkdir /home/data
```
i think you need sudo

```
sudo mkdir /home/data
```

---

### Post by philinux on 2007-12-23
No you dont. Its your own home folder. :lolflag:

---

### Post by seventhc on 2007-12-23
> **philinux said:**
> No you dont. Its your own home folder. :lolflag:
I tried it, permission denied b/c it isnt getting written to your own <username> it's getting written in the file system next to your <username> folder
so sudo mkdir /home/data :guitar:

```
j0hn@cipher:~$ pwd
/home/j0hn
j0hn@cipher:~$ mkdir /home/data
mkdir: cannot create directory `/home/data': Permission denied
j0hn@cipher:~$ sudo mkdir /home/data
[sudo] password for j0hn:
j0hn@cipher:~$ cd /home
j0hn@cipher:/home$ ls
data  j0hn  seventhc
j0hn@cipher:/home$ pwd
/home
j0hn@cipher:/home$ cd
j0hn@cipher:~$ 
```

---

### Post by philinux on 2007-12-23
The only reason I posted that is because I tried it first even though I knew it was correct. No problem.

---

### Post by HermanAB on 2007-12-23
Hmm, some misinformation in this thread...

You cannot make a directory on a device.  Therefore you cannot make a directory called /dev/hda/anything.

You need to make a directory on a file system.  In this case, you have a file system mounted as /home.  Therefore, you can make a directory called /home/data, but you need to have super user privileges to do that:
$ sudo mkdir /home/data

Next, you want to be able to access that data, so you need to change the ownership to yourself (joesixpack):
$ sudo chown joesixpack:joesixpack /home/data

Now, joesixpack can access /home/joesixpack (your home directory), as well as the data directory /home/data.

'Hope that helps!

Herman

---

### Post by seventhc on 2007-12-23
> **philinux said:**
> The only reason I posted that is because I tried it first even though I knew it was correct. No problem.
oh..lol:lolflag: how was I supposed to know:popcorn:

edit...wait...did you create it without sudo????

---

### Post by philinux on 2007-12-23
Why would anyone need super user privileges to create anything in your own home folder.

See screenshot no error folder created.

---

### Post by jaybombalous on 2007-12-23
> **philinux said:**
> Why would you anyone need super user privileges to create anything in your own home folder.

See screenshot no error folder created.


your own /home/user folder is your user name.

/home is not **your** home directory, its the /home directory that contains directories of all the user's. They are filed under /home so its easy to understand and find in the / directory.

U have to use sudo to access anything that is not /home/username/* or ~/*

my /home folder has only root permissions, if yours is different then its **wrong!**


If I was the thread starter I would add all the users I want to be able to access /home/data to a group. Give rw access to that group of the /home/data folder. easy fix and it would work perfectly well still preserving proper security measures. If /home has permissions for anyone except root then any user could potentially delete any other users account, does that sound plausible for a tight security? Like I said above, your setup is wrong!

---

### Post by seventhc on 2007-12-23
deleted...

---

### Post by philinux on 2007-12-23
I only have one user. Permissions in /home get created as my user.

i did move it to its own partition, you know psychocat thing. Maybe its not wrong but different

[edit] somehow my /home folder got chowned to my user in the process I think.

---

### Post by jaybombalous on 2007-12-23
> **philinux said:**
> I only have one user. Permissions in /home get created as my user.

i did move it to its own partition, you know psychocat thing. Maybe its not wrong but different


yes, different then the** default** ubuntu install which makes it a security threat. But, as u may have guessed the thread starter probably doesn't use psychocats webpage to alter his install, all he wants its to be able to share some files amongst users with the default ubuntu install.

That requires he uses sudo, which is the right way. NOW STOP SPREADING MISINFORMATION. **your setup is different then his and in no way should your setup reflect the way his should work out of box.**

I think ubuntu is great, but its starting to get sloppy with all the 3rd party tweaks and hacks floating about.

---

### Post by philinux on 2007-12-23
Hardly a security threat. LMAO. One user on one pc :lolflag:

Chil Peace etc.

---

### Post by jaybombalous on 2007-12-23
> **philinux said:**
> Hardly a security threat. LMAO. One user on one pc :lolflag:

Chil Peace etc.



typical asshat response, lame! now where is your serious rebuttal?

the security threat comes when he tries it your way and he has more then one user. His kid decides to have a look and clicks delete on **his** home folder. Great! guess u wasn't so brilliant after all.

its not just your box moron its someone else's and they may not share your attitude.

---

### Post by sd_smoker on 2007-12-24
Geez, I step out for a few hours and look what happens! ;-)

Anyway, I was able to create the folder using "sudo mkdir /home/data" and I can access it with both my user and my wife's user. I haven't tied writing to it yet. I'll probably end up creating a group and giving it rw permissions as suggested a while back.

Anyone care to take a stab at my question back in post #6 about an option for cp that automatically creates sub-folders if they don't exist in the destination?

Thanks guys!

---

### Post by philinux on 2007-12-24
Apparently having my box configured differently is a cardinal sin now. I thought this was what linux was not about.

Anyway for cp this is great.

[http://www.oreillynet.com/linux/cmd/cmd.csp?path=c/cp](http://www.oreillynet.com/linux/cmd/cmd.csp?path=c/cp)

Merry Xmas and peace to all.

---

### Post by sd_smoker on 2007-12-24
That's essentially the same thing I see when I run "man cp". I'm getting an error saying the first sub-folder does not exist so I assumed there would be an option to create sub-folders automatically. If it's there, I'm not seeing it. Am I misdiagnosing the problem?

---

### Post by argie on 2007-12-24
Guys, calm down. This is a fairly simple task and there's little reason to go jumping at each other's throats. Here is your solution, OP: (skip to the relevant part)

First, create a directory in the /home folder: (you will need sudo because this is NOT your home folder, your home folder is /home/username. I would recommend /media but I'm going according to what you want here)
```

sudo mkdir /home/data

```

Now copy your files:
```

sudo cp -r /media/hda1/Documents\ and\ Settings/All\ Users/Documents/My\ Music/ /home/data/Music

```

The reason the cp command was not working was:

1. When you say **cp /Documents And Settings/** the computer sees '/Documents' as the first parameter and 'And' as the second parameter. You can avoid this by enclosing the entire path in quotes or by using the \ character to 'escape' the space so that it is no longer counted as the end of the first parameter.

2. When you use the -r parameter, the cp command acts recursively. The * character is unnecessary and wouldn't work anyway in a cp command. 

3. The * character does not work in a cp command. You will need to either use xargs to redirect the output from ls, or, more sensibly, use a for loop to select each file and copy it to its destination. The for loop can allow you a large degree of control, you can copy only the music that has a certain id3 tag, for instance. There are many tutorials on this on the web, and though I've done it myself many times, I don't know quite enough to explain it as well as them. **Correction**: Funny, it does seem to work. I just checked. It didn't the last time. Anyway, you do not need the * for this case.

4. There is no need to type out the entire path from memory. Do the following:
Type cp, type /media/hda1/Documents, hit the tab key now and if there is nothing else that starts with Documents it will complete that part of the path for you. Repeat the process by typing out more bits of the path and hitting the tab key. This will get you the right path more often than trying to remember it from memory. As a bonus it will perform all the escaping by itself.

---

### Post by sd_smoker on 2007-12-24
Thank you! I'll give this a shot as soon as I get home...

So I guess the "Directory does not exist" error was because it was looking for a directory called "*" ...doh!

---

### Post by argie on 2007-12-24
> **sd_smoker said:**
> Thank you! I'll give this a shot as soon as I get home...

So I guess the "Directory does not exist" error was because it was looking for a directory called "*" ...doh!

Almost, but not quite. It stops reading the path at /media/hda1/Documents because there's a space there. So it thought that your origin directory was /media/hda1/Documents.

---

### Post by sd_smoker on 2007-12-24
Ah, I should have clarified that I didn't actually run the command in my initial post (that was just speculation). I ran the command I included in post #6:

cp -r "/media/hda1/Documents and Settings/All Users/Documents/My Music/*" "/home/data/Music/"

---

### Post by sd_smoker on 2007-12-24
Okay, I am able to copy files into the new directory, but I cannot access them since they were created as root. I assume I just need to run a simple command or two to change the permissions on the folder (and sub-folders). The trick here is that I need myself and my wife to be able to have wrx permissions on this folder and everything in it. So what commands will I need to run in order to accomplish this?

Would a simple "chmod 777 /home/share" do the trick? Keep in mind I need all future folder/files added to this folder to inherit these permissions as well...

---

### Post by argie on 2007-12-25
> **sd_smoker said:**
> Okay, I am able to copy files into the new directory, but I cannot access them since they were created as root. I assume I just need to run a simple command or two to change the permissions on the folder (and sub-folders). The trick here is that I need myself and my wife to be able to have wrx permissions on this folder and everything in it. So what commands will I need to run in order to accomplish this?

Would a simple "chmod 777 /home/share" do the trick? Keep in mind I need all future folder/files added to this folder to inherit these permissions as well...

Ah, of course, I forgot. You can do that, it'll work. But, even better, you could change the directory's owner to you. That way you can change the permissions easily from Nautilus later, if you so wish.

```
sudo chown j0hn:j0hn /home/data
```

I took the username from that reply on the first page. You'll have to change that bit if it's different.

---

### Post by sd_smoker on 2007-12-25
Thanks, although I imagine I'll want create a group and give that group ownership of that folder since I need multiple users to have read/write permission. Hopefully that won't be too hard to do...

---

