---
title: "mkdir does not work"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Jordan Meeter on 2006-10-05
Just for the heck of it, I am using the terminal do make a new directory in my home folder. I figured I am new to Linux, so I might as well use the terminal and learn someting. Here is what I did:

```
jordan@jordan-desktop:~$ mkdir /photos/
mkdir: cannot create directory `/photos/': Permission denied
jordan@jordan-desktop:~$ sudo mkdir /photos/
Password:
jordan@jordan-desktop:~$
```

I went to Places > Home Folder and 'photos' is not there. What did I do wrong?

[Edit] I figured I would try it one more time, then I did this:

```
jordan@jordan-desktop:~$ mkdir /photos/
mkdir: cannot create directory `/photos/': File exists
jordan@jordan-desktop:~$ ls
Desktop  easyubuntu  Examples
```

It *says* the folder exists, but does not appear even when I do ls.

---

### Post by mitch.c on 2006-10-05
> **Jordan Meeter said:**
> Just for the heck of it, I am using the terminal do make a new directory in my home folder. I figured I am new to Linux, so I migth as well use the terminal. Here is what I did:

```
jordan@jordan-desktop:~$ mkdir /photos/
mkdir: cannot create directory `/photos/': Permission denied
jordan@jordan-desktop:~$ sudo mkdir /photos/
Password:
jordan@jordan-desktop:~$
```

I went to Places > Home Folder and 'photos' is not there. What did I do wrong?
Your command is trying to create photos in /. Your syntax needs to be:
```
mkdir ~/photos
```
When you ran with sudo, you succeeded in creating the photos folder in /

---

### Post by Jordan Meeter on 2006-10-05
So how can I delete that folder?

---

### Post by mitch.c on 2006-10-05
> **Jordan Meeter said:**
> So how can I delete that folder?
```
sudo rmdir /photos
```

---

### Post by bodhi.zazen on 2006-10-05
> **Jordan Meeter said:**
> Just for the heck of it, I am using the terminal do make a new directory in my home folder. I figured I am new to Linux, so I might as well use the terminal and learn someting. Here is what I did:

```
jordan@jordan-desktop:~$ mkdir /photos/
mkdir: cannot create directory `/photos/': Permission denied
jordan@jordan-desktop:~$ sudo mkdir /photos/
Password:
jordan@jordan-desktop:~$
```

I went to Places > Home Folder and 'photos' is not there. What did I do wrong?

[Edit] I figured I would try it one more time, then I did this:

```
jordan@jordan-desktop:~$ mkdir /photos/
mkdir: cannot create directory `/photos/': File exists
jordan@jordan-desktop:~$ ls
Desktop  easyubuntu  Examples
```

It *says* the folder exists, but does not appear even when I do ls.

Your prpblem has to do with the leading slash, or relative vs. absolute path.

In your home directory:


jordan@jordan-desktop:~$ mkdir /photos/ will give you a directory, photos, in root, /
ls / and you may see it (you may have permission problem).

jordan@jordan-desktop:~$ mkdir photos is what you want.

---

### Post by Jordan Meeter on 2006-10-05
Ok, thanks a lot!

One other question: I know it would be a lot easier to just drag and drop a folder off my CD, but just for experience I'd like to use the terminal. How can I copy the folder "Pictures" off my CD into my folder 'photos' that I just created?

---

### Post by bodhi.zazen on 2006-10-05
> **Jordan Meeter said:**
> Ok, thanks a lot!

One other question: I know it would be a lot easier to just drag and drop a folder off my CD, but just for experience I'd like to use the terminal. How can I copy the folder "Pictures" off my CD into my folder 'photos' that I just created?

cp <path_to_pictures_on_cd>/* ~/photos

Example (adjust to your path):
```
cp /media/cdrom/pictures/* ~/photos
```

---

### Post by Jordan Meeter on 2006-10-05
Darnit, I had the name wrong. The name on the disc is 'My Pictures'. I tried ```
jordan@jordan-desktop:~$ cp /media/cdrom0/My Pictures/* ~/photos
``` and got ```
cp: cannot stat `/media/cdrom0/My': No such file or directory
cp: cannot stat `Pictures/*': No such file or directory
```

I tried it with an underscore as well, got ```
cp: cannot stat `/media/cdrom0/My_Pictures/*': No such file or directory
```

---

### Post by bodhi.zazen on 2006-10-05
> **Jordan Meeter said:**
> Darnit, I had the name wrong. The name on the disc is 'My Pictures'. I tried ```
jordan@jordan-desktop:~$ cp /media/cdrom0/My Pictures/* ~/photos
``` and got ```
cp: cannot stat `/media/cdrom0/My': No such file or directory
cp: cannot stat `Pictures/*': No such file or directory
```

I tried it with an underscore as well, got ```
cp: cannot stat `/media/cdrom0/My_Pictures/*': No such file or directory
```

You need to "escape" the "white space". Linux does not like the space in your command.

Use this:```
jordan@jordan-desktop:~$ cp /media/cdrom0/My\ Pictures/* ~/photos
```

the \ is the Linux way.

Next, let me show you tab completion

Start typing, use the <tab> key.

Ex cp /me<tab> gives you -> cp /media

Now cp /media/cdrom0/My<tab> give you cp/media/cdrom)/My\ Pictures ....

This works for commands as well.

Makes life easier.

---

### Post by CatKiller on 2006-10-05
Make use of Tab-completion in paths. So cp /med<tab>cdr<tab>0<tab>My<tab> will fill in the correct path for you. Otherwise, cp /media/cdrom0/My\ Pictures/* ~/photos will sort out that nasty space.

Edit: beaten to the punch :)

---

### Post by bodhi.zazen on 2006-10-05
> **CatKiller said:**
> Make use of Tab-completion in paths. So cp /med<tab>cdr<tab>0<tab>My<tab> will fill in the correct path for you. Otherwise, cp /media/cdrom0/My\ Pictures/* ~/photos will sort out that nasty space.

Edit: beaten to the punch :)

Hate it when that happens! :lol:

---

### Post by Jordan Meeter on 2006-10-05
Hmm, that worked for all of the *files*... How do I move all of the *folders* in My Pictures?

---

### Post by CatKiller on 2006-10-05
> **Jordan Meeter said:**
> Hmm, that worked for all of the *files*... How do I move all of the *folders* in My Pictures?

The command cp -R ... will recursively copy the files and directories. **man cp** will tell you lots of things about the copy command.

I don't mean to scare you, but a friend of mine suggested that the command ```
( cd *<source>* && tar clf - . ) | ( cd *<dest>* && tar xvpf - )
``` was the way to go with big copy processes. I doubt that it will be necessary for this particular copy operation, though.

---

### Post by DirtDawg on 2006-10-05
> **CatKiller said:**
> 
I don't mean to scare you, but a friend of mine suggested that the command ```
( cd *<source>* && tar clf - . ) | ( cd *<dest>* && tar xvpf - )
``` was the way to go with big copy processes. I doubt that it will be necessary for this particular copy operation, though.

Jesus that scares *me*.

---

### Post by CatKiller on 2006-10-05
> **DirtDawg said:**
> Jesus that scares *me*.

LOL. I was using it for moving an entire filesystem from one partition to another, and he trusted tar to do the right thing a lot more than he trusted cp. I never did establish exactly why. I suppose that if you were doing it over a network or something you could even put in a compression/decompression option. Could be useful.

---

### Post by Frak on 2006-10-05
> **Jordan Meeter said:**
> Just for the heck of it, I am using the terminal do make a new directory in my home folder. I figured I am new to Linux, so I might as well use the terminal and learn someting. Here is what I did:

```
jordan@jordan-desktop:~$ mkdir /photos/
mkdir: cannot create directory `/photos/': Permission denied
jordan@jordan-desktop:~$ sudo mkdir /photos/
Password:
jordan@jordan-desktop:~$
```

I went to Places > Home Folder and 'photos' is not there. What did I do wrong?

[Edit] I figured I would try it one more time, then I did this:

```
jordan@jordan-desktop:~$ mkdir /photos/
mkdir: cannot create directory `/photos/': File exists
jordan@jordan-desktop:~$ ls
Desktop  easyubuntu  Examples
```

It *says* the folder exists, but does not appear even when I do ls.
I have had that many times, it means use SUDO,
and if your hands get tired, run (sudo -i) (not recommended)
that will put you in root mode.

---

