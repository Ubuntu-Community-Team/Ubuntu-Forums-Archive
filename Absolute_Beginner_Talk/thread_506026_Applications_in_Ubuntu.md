---
title: "Applications in Ubuntu?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-07-21
I am new to the Linux platform, and Ubuntu is my first.

So I was wondering... Where are applications installed on the computer?

I am running the latest version, Feisty Fawn.

Also just a side note, how can I rename my main hard disk? The system wont let me.

---

### Post by meborc on 2007-07-21
there are 2 main ways to see where the programs are installed on your machine... 

1) go to synaptic... search for the program you installed... right-click properties... files... (if i remember correctly)

2) open terminal and type "locate <package>"... same result

to understand the linux file system and how folders tree is built up, read this - [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Smu on 2007-07-21
hi and welcome to Ubuntu! I had the same experience as you when I first started using ubuntu. Felt like I was lost when I couldn't find my  /Program Files folder... As this folder is quite essential in windows.

The ubuntu programs are stored in /usr/bin, but I've found out that I rarely need to check it out, because almost 100% of all  programs automatically gets into the application launcher, and if you install using synaptic uninstalling is just a matter of unchecking a box. Another thing that I was worried about when i first started with ubuntu was that I'd run out of space with all mi installed programs, but this is infact quite unlikely because the ubuntuprograms tend to be exeptionally small compared to windowsprograms.

---

### Post by Al3xK3aton on 2007-07-21
The key to remember is that it isn't Mac OS X, you can't just double click a program and BAM!!!! it works. It installs into a separate directory, like Windows.

---

### Post by swoll1980 on 2007-07-21
> **Al3xK3aton said:**
> The key to remember is that it isn't Mac OS X, you can't just double click a program and BAM!!!! it works. It installs into a separate directory, like Windows.

whats with the sarcasam?

---

### Post by Cheese Roller on 2007-07-21
Well, the thing is...

I tried to install two programs already, Firefox and Pidgin and after I extract the .tar.bz2 file to my desktop (since I have no clue where to extract it) then the file just kind of sits there and I want to get it where it needs to go.

Where should I extract to?

---

### Post by mlentink on 2007-07-21
Cheese,

I really think it would be worth your while to have a look at the top sticky in this forum. Also[ this ]("http://monkeyblog.org/ubuntu/installing/")might help you in learning how things are installed in Ubuntu.

---

### Post by Koybe on 2007-07-21
You should avoid .tar.bz2 and .tar.gz files for installation. These are generally sources files that you'll need to compile to get it working.

To make installation on ubuntu you'd better get .deb files which are installed automatically. But the real best way is using synaptic package manager or add/remove application as it was tell before.

Here is a nice link explaining all that : [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

The program you're trying to install :
Firefox - is already included in it's last version. No need ton install anything.
Pidgin - You can find it already installed (still called GAIM in Applications->internet). If you really want Pidgin and can't stay with GAIM, you can find the .debs here : [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

@mlentink : burned ;)

---

### Post by Cheese Roller on 2007-07-21
Yeah, that is what a lot of people tell me...

But what if that file is unavailable for a program I want?

---

### Post by Malibu Illusion on 2007-07-21
Then compile it from source?

.tar.gz files are better known as "tarballs."  They are the source of an application.  You can compile them, generally, by extracting them:

```
tar -zxvf name.tar.gz
```

Then running through a config:

```
./configure
```

Building them:

```
make
```

And finally installing them:

```
sudo make install
```

You need packages installed such as build-essential to do this, as well as the ability to manually resolve any depandancy issues that you come up against, which often require other things to be installed.

There are resources about these topics; you've already been linked to one in this thread by mlentink.  Check it out.

---

### Post by Koybe on 2007-07-21
And this : [http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source) as given before.

---

### Post by Cheese Roller on 2007-07-21
> **Malibu Illusion said:**
> Then compile it from source?

.tar.gz files are better known as "tarballs."  They are the source of an application.  You can compile them, generally, by extracting them:

```
tar -zxvf name.tar.gz
```

Then running through a config:

```
./configure
```

Building them:

```
make
```

And finally installing them:

```
sudo make install
```

You need packages installed such as build-essential to do this, as well as the ability to manually resolve any depandancy issues that you come up against, which often require other things to be installed.

There are resources about these topics; you've already been linked to one in this thread by mlentink.  Check it out.

Okay I typed that into the Terminal. Directory not found, it's right on my desktop.

Sorry about being such a n00b, it's just that Linux is so different to me...

---

### Post by 3rdalbum on 2007-07-21
Yes, Linux is so different to everyone. It's more different than Windows is to Mac.

Cheese Roller, until you've been using Linux for a couple of months, I suggest you avoid trying to compile software. It's not actually difficult, it's just "involved" and really unneccessary until you've explored a large amount of what's in the repositories.

Go to Synaptic Package Manager and just have a browse, download whatever piques your interest.

---

### Post by mikewhatever on 2007-07-21
Either precede the commands with > cd /home/your_user_name/Desktop
or move the tar to your home directory and try again.
Isn't firefox preinstalled in Ubuntu?

---

### Post by Cheese Roller on 2007-07-21
> **mikewhatever said:**
> 
Isn't firefox preinstalled in Ubuntu?

Mine wasn't the highest version.

Anyway, I am also trying to install pidgin. I typed in all the codes you said, but then I got this message.


```
gzip:stdin: not in gzip format
tar: Child returned status 1
tar: error exit delayed from previous errors
```

What does this mean?

Everyone is saying to avoid .gz applications for some reason, but the thing is that every single file I find ends in that suffix. I don't see any .deb files, and I would really like my Linux to have some functionality to it.

---

### Post by Majorix on 2007-07-21
In your place I would do as suggested and stick to Synaptic applications.

Firefox is now the latest version in the repos (2.0.0.5).

Instead of Pidgin you could use Gaim, which offers almost the same, but is an older version.

If you MUST get debs, then go to [www.getdeb.net](www.getdeb.net)

---

### Post by Nekiruhs on 2007-07-21
> **Cheese Roller said:**
> Mine wasn't the highest version.

Anyway, I am also trying to install pidgin. I typed in all the codes you said, but then I got this message.


```
gzip:stdin: not in gzip format
tar: Child returned status 1
tar: error exit delayed from previous errors
```

What does this mean?

Everyone is saying to avoid .gz applications for some reason, but the thing is that every single file I find ends in that suffix. I don't see any .deb files, and I would really like my Linux to have some functionality to it.
Is there any particular feature you need/want in the new version? Any reason for updating that is essential?

---

### Post by gigaferz on 2007-07-21
[http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)

here is pidgin, youll need the two packages

---

### Post by coolen on 2007-07-21
> **Cheese Roller said:**
> Yeah, that is what a lot of people tell me...

But what if that file is unavailable for a program I want?

Just thought I'd let you know, the Ubuntu repositories aren't the only ones. Anyone can create their own repository if they want. Try looking for a repository that contains the program you want first. Chances are someone's made one.
Barring that, .debs are the best way to go. They'll install the program fine, and you'll get dependencies resolved (assuming they're available through your repositories), but you won't be able to automatically upgrade. Removal and such will work just fine, though.
Tarballs are your final resort. If you install a program from source, you'll have to manually resolve any dependencies, which was a problem that plagued early Linux users. Your system will also be unaware of the program, so to speak...the APT system won't know it's there. If you download a program that conflicts with another you installed from source, APT will not know this, and you could break your system.

Firefox and Gaim are both kept at fairly recent versions (Pidgin is simply Gaim's new name) in the repositories. Are you upgrading for any specific functionality, or do you just enjoy life on the bleeding edge?

---

### Post by koganinja89 on 2007-07-21
> **swoll1980 said:**
> whats with the sarcasam?

chown mine /B**ch

---

### Post by Cheese Roller on 2007-07-21
Hey guys, thanks a lot for teaching me stuff.

I installed debs of all the programs I wanted at the moment from that website you gave me.

Here's a new question.

Now that I have pidgin...

How do I get rid of GAIM?

---

### Post by Majorix on 2007-07-21
Apps > Accessories > Terminal then paste in these:

```
sudo apt-get remove gaim
sudo apt-get remove gaim-data
```

---

### Post by Cheese Roller on 2007-07-21
I typed that in.

then it asked me if I was root, I said yes.

Then it gives me a password field, but will not let me type.

---

### Post by Cheese Roller on 2007-07-21
bump

---

### Post by Cheese Roller on 2007-07-21
bump again

---

### Post by mikewhatever on 2007-07-22
It does let you type, but does not print the password. Just type it and hit Enter.

---

### Post by coolen on 2007-07-22
> **Cheese Roller said:**
> I typed that in.

then it asked me if I was root, I said yes.

Then it gives me a password field, but will not let me type.

Yeah, don't worry. You are typing, it's just not giving you any visuals on that.
A little wierd to get used to, I know. I sat there for about ten minutes on my first Linux install (I didn't have a GUI after the install), wondering what the heck was going on.
Just a little added security.

---

### Post by spyros71 on 2007-07-22
> **Majorix said:**
> In your place I would do as suggested and stick to Synaptic applications.

Firefox is now the latest version in the repos (2.0.0.5).

Instead of Pidgin you could use Gaim, which offers almost the same, but is an older version.

If you MUST get debs, then go to [www.getdeb.net](www.getdeb.net)


WOW !!! this is a great site. Thanks for sharing Majorix !!

---

