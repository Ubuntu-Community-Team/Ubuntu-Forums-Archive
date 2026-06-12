---
title: "Trouble with Adobe Reader FileOpen Plug-in..."
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by incen on 2008-02-28
Hi, guys (well, probably some girls, I was called a man, which I'm not :p),
I got some problems with opening some PDF files. They are so Adobe-oriented so that I have no way to open them in evince. However, they require some FileOpen Plug-in.

This is what I've done:
To get medibuntu:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Then, to install acroread:
```
sudo aptitude install acroread
```

However, I still couldn't open those files. Acroread told me there is some plug-in missing. So I did:
```
sudo aptitude install acroread-plugins
```

But not I still cannot open them!!!

This is what it says on their site:
> Get the plugin here for Adobe Reader 7, or here for Adobe Reader 8. Move it to your Adobe Reader plug_ins directory and make it executable. Create a directory named ".fileopen" in your home directory and make sure it is writeable by you. That is all!
I downloaded the plugin they have. It's a *.api. How do I make it executable?
Thanks in advance!

---

### Post by pytheas22 on 2008-02-28
To make it executable right click on the file, select the Properties tab, and check the box that says "Allow executing of this file as a program" or something close to that.

---

### Post by incen on 2008-02-28
Ha, thanks!!! I actually found a site to tell me how to change it. It's basically a chown thing. Hoo~ took me so long time to figure this out. Also, I dug into those directories and finally got to know where acroread really is. The link stuff is really confusing.

---

### Post by incen on 2008-02-29
I also need to make Acrobat Reader as the default reader in Firefox. Can anyone tell me how to set this? I check Preference in Firefox but have no luck. :(

Please~~ thanks!

---

### Post by pytheas22 on 2008-02-29
I don't know how to do that; probably you would have to change something in about:config.  As a workaround, couldn't you just save the files to your desktop and open them from there using Adobe Reader?

---

### Post by incen on 2008-02-29
I'm so glad you replied my thread!!! I almost think it's hopeless. :p
I did so. However, I still cannot open the files. It's sort of a security thing, I think. In acroread, there's a Help -> About Adobe Plug-ins. However, although I put FileOpen plugin under the plugin folder. It's still not detected. :(

---

### Post by pytheas22 on 2008-02-29
Sounds like a problem with permissions.  Try doing this:

1. open a terminal and cd to the directory where the plugin file is located.  Based on your first post, I think that this is .fileopen, so:

```
cd .fileopen
```

2. then make the permissions super unrestrictive:

```
chmod 7777 FileOpen
```

3. for good measure, we'll do the same thing to the directory itself:

```
chmod 7777 ~/.fileopen
```

(if the name of the file in question is not FileOpen, change the command as needed)

then see if it works.  Keep in mind that you should almost never set permissions to "chmod 7777," because it gives anyone the permission to do anything with the file, but you can at least do this temporarily to see if it makes the program work, and then we can scale the permissions back to only allow what you need.

---

### Post by incen on 2008-03-03
Thanks for reply! I'll try this once I get to my Lab PC. Well... however, I think I create the folder, ./fileopen with my own user not as root. Anyway, i'll try it. Thanks! ^^

---

