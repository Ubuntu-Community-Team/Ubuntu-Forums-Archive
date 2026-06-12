---
title: "Beginners questions - again"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by jambalaya on 2008-02-14
Hi, I am new here so:
Hello Everyone!

Now, down to business.

I have a few questions regarding my new OS. They are downwards. Note however that I am booting Kubuntu, so if any of these question simply dosn't general enough to be asked here, just ignore them.

1. I am quite new, but I like to know things and have a lot of time, so I want to learn and explore. First off, I would like to learn about the filesystem in linux - what all the /opt, /var, /proc, and so on mean. And what's the difference between /bin, /usr/bin, and /usr/local/bin. What's put in /opt, and what in /lib, what in /usr/lib and so on. Is there any tutorial that would tell me the basics?

2. when I press CTRL+ALT+F1-F6, I would expect a terminal; this doesn't happen, however. All I see  is a blank black screen, with the cursor blinking in the top left corner, I guess this is where the prompt would go. Can anyone help me with that? If anyone is willing, please ask any questions concerning my hardware and configuration. I tried to search for the answer but I don't really know what to look for. The strange thing is I have no problems with graphics mode, as some people, but with switching to the console. ALT+F7 goes back to KDE normally.

3. in /dev, there are a lot of files (devices?) - what are these: ptya(number), ptyb(number), ttyab and so on?
and about /media - I have a dvd recorder but there is a /media/cdrom mount (is this correct naming?), and I think I read somewhere that there can be /media/dvd or even /media/dvdwriter(recorder) - what does this mean and how can I install my dvdwriter? (it works fine in K3B)

4. and last thing (for now ;-)): I was able to do "echo something >> /media/cdrom" with no error (as sudo) - what does this call even mean? I thought I would start doing some kernel-level recording or something, but the file just sat there in that directory

Other than that, I am really impressed at the amount of work you guys did with the distro! I did try some 5.10 on the same machine and it didn't work well, but this changed now, so that I even went mad and removed the other OS I had, and I am perfectly satisfied with the choice - I mean, some of you may laugh how I can be satisfied without basic knowledge, but I didn't use the other OS on a professional level either, and so far I haven't longed for anything I had there at all. And I could find many many answers at this site and others, so this is great!

Cheers.

---

### Post by dca on 2008-02-14
On the file system question:
 
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Thingymebob on 2008-02-14
Question 2 is a bug
see this thread [http://ubuntuforums.org/showthread.php?t=595825]("http://ubuntuforums.org/showthread.php?t=595825") No Virtual terminals in Gutsy is the first bug listed

---

### Post by finer recliner on 2008-02-14
4) the ">>" operator means "append to the existing file specificed after it. 

so, if you had a file called test.txt that looked like this:
```

hello
world

```
and then ran the following command:
```
echo blah >> test.txt
```
test.txt would be modified to look like this:
```

hello
world
blah

```

however you seem to be using it illegally. most people's /media directory only contain more directories for storage devices to be mounted like hard drives, flash drives, and optical drives. sometimes you'll see a symbolic link (the equivalent for a shortcut in windows) for the cdrom or something (but even that just points to another directory). it is illegal to use the >> operator with a directory. 

to find out what format a filename is (i.e. directory, symbolic link, plain text, PDF, executable, etc...) use this command:
```
file <filename>
```

so i dont know why you're able to write to '/media/cdrom'. make sure you posted the exacte command you used correctly.

---

### Post by jambalaya on 2008-02-14
I know what code means, but thanks ;-)

about the command itself - it was my mistake, sorry
the command is:
```

echo something >> file

```
while im in /media/cdrom; I also have to su,  sudo gives me "bash: file: Permission denied"
but after I su, the file is created fine and contains the "something" line

about /media/dvd or cd/dvdrecorder - is this valid claim that I have seen it somewhere?

Thanks.

---

### Post by jambalaya on 2008-02-14
Thanks for the links about the filesystem.

A little update on the F1-6 ttys:
I removed vga=792 from /boot/grub/menu.lst and now I have them, but it acts a little differently on boot; namely, before (with vga on) the usplash showed immediately, now the first things I see are some magic letters, and then the splash screen shows up; so I guess I fixed it ;-) but I don't know exactly what I did - what does removing this vga snippet mean? I can see the splash screen allright

Apart from that, now sometimes I can see vertical white lines on the virtual consoles (not the whole screen, just a few lines), looks strange, like an error on the screen or something, but this is minor, I guess

Regards

---

