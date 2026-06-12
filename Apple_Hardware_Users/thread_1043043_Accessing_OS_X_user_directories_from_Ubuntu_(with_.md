---
title: "Accessing OS X user directories from Ubuntu (with a bonus question regarding cd)"
date: 2009-01-18
forum: Apple Hardware Users
---

### Post by Audacitor on 2009-01-18
Hey all,

I'm fairly new to Ubuntu. I'm a Mac geek by trade, you see, so most of my knowledge of the command line is from Unix, and even then, my knowledge of the command line is limited.

I'm very, very in love with OS X, and I know for certain I won't be dropping it any time soon. What I want to do is get my Ubuntu installation to 'play nice' with OS X. By that, I mean set them both up in such a way that switching between them doesn't limit me very much.

Right now, I want to create aliases (I think in Linux world, you call them file links, or symbolic links) for all my OS X user directories (Music, Movies, Documents, and so on) in my corresponding Linux user directory.

In this manner, I could set things like Amarok and Transmission up to simply write and read from my OS X user directories. Then, when I switch between OS X and Ubuntu, I can still access my music and torrents and what not.

However, I don't have permission to get into my OS X user directories (which is good; that's how it's supposed to work). I couldn't find anyway of authenticating using Nautilus, so I pulled up a terminal to see if I could see and/or navigate the contents of my OS X user directories that way.

Using sudo, I can ls the contents of my user directories, but a peculiar thing happened when I tried to sudo cd. It told me the command wasn't found.

I know what this means, so my next logical step was to see if the man page existed. It didn't.

So next I want to the Package Manager and found the coreutils package, which didn't list cd among it. Well, at least now I knew nothing that was supposed happen didn't.

So, how can I make aliases tying into my OS X user directories, and what's up with cd? Is there a Linux alternative I don't know about and can't find (the official docs explained cd)?

---

### Post by Achetar on 2009-01-18
sudo is not allowed to run cd. you must sudo su root and then you can use cd.

You should probably setup a static mount in fstab to prevent your links from becoming invalid. To link files to your /home directory:
```

$ sudo ln -s /media/disk/User/Audacitor ~/OSX

```
that will create a symlink from the User Audacitor's Mac OSX directory to the /home/audacitor/OSX directory. Assuming that Audacitor and audacitor are your usernames.

references:
```

$ man ln
$ man fstab
$ man mount
$ man useradd

```

---

### Post by TreeHugger52 on 2009-01-18
Ubuntu will not be able to write to journaled hfs+ partitions. It's just not going to happen. Journaling is the problem, not hfs+. You could turn off journaling (probably not a good idea), or create another partition that both OS's can read and write (FAT32 maybe) to store files that both OS's can access.

I realize that doesn't answer your question about symbolic links, but this may be the underlying problem.

---

### Post by Achetar on 2009-01-18
Good info TreeHugger. The only common FS for Mac/Linux really is FAT32. This is most unfortunate....

---

### Post by cyberdork33 on 2009-01-18
Once you get the file system mounted, you can change your Ubuntu uid to match the one in OSX, then it is appear that the files belonging to your OSX user also belong to your Ubuntu user.

---

### Post by Audacitor on 2009-01-18
Thanks for the help, all.

@Achetar: I can make the symlinks alright, but it doesn't change my ability to read/write to my OS X files (more on this in a bit).

@TreeHugger: I was really hoping I wouldn't have to do something like disabling journaling. I have a Time Capsule that maintains hourly backups, so I suppose I should be relatively safe. Still...

@cyberdork: My OS X uid uses capital letters, which doesn't seem possible in Ubuntu.

In OS X, if you try to do a file operation you're not allowed to do, it will ask for an administrator name and password. Is there nothing similar on Ubuntu?

---

### Post by cyberdork33 on 2009-01-18
> **Audacitor said:**
> @cyberdork: My OS X uid uses capital letters, which doesn't seem possible in Ubuntu.
uid != username

A uid is an id number for your user account.

> **Audacitor said:**
> In OS X, if you try to do a file operation you're not allowed to do, it will ask for an administrator name and password. Is there nothing similar on Ubuntu?
maybe, but not by default. If you want to perform an administrator action, you must prepend the command with sudo.

---

### Post by Audacitor on 2009-01-18
> uid != username


Ah, my mistake; I thought it was just a difference in terminology.

> If you want to perform an administrator action, you must prepend the command with sudo. 

I meant in OS X it's done graphically. Dragging a file into a system folder brings up a dialog box.

---

### Post by cyberdork33 on 2009-01-19
> **Audacitor said:**
> I meant in OS X it's done graphically. Dragging a file into a system folder brings up a dialog box.
I understand, hence the reason for the first part of my reply which you did not quote. gksudo is the "graphical" equivalent to sudo.

---

