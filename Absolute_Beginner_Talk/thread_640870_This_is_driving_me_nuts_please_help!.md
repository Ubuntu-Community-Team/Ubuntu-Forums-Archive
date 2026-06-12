---
title: "This is driving me nuts please help!"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Mular on 2007-12-14
Hey Guys just recently switched over to linux, I am trying to learn how to use the sudo mount command.. So far so good but I have one issue..

I am mounting via gnome-terminal and I really like doing it that way - but everytime I try to do it and use TAB complete I get this annoying error.. I will post it 

mular@AlphaLinux:/media/Local Disk/Games/Warcraft III/Warcraft III and The Frozen Throne$ sudo mount Warcraft\ III\ -\ The\ Frozen\ Throne\ \[Diskgrep: Trailing backslash
grep: Trailing backslash    

And it does it constantly.. I don't know if its a bug or intended but I rarely have the issue with anything other then mount..

Is there another way of going about what I am trying to do?

Ultimately I am trying to run a game with wine without using the cd but thats not working out. So I am trying just to mount the game since it is in iso format..

I been using sudo mount -o loop <iso locations> <mnt point>

While we are on this topic what does -o mean, and loop as well? Is that an acceptable away of mounting? I also seen people use iso9660 - whats up with that should I be doing that?

---

### Post by llamakc on 2007-12-14
Type:

sudo mount "Warcraft {AND then try tab complete and end with a closing} "

---

### Post by Mular on 2007-12-14
That doesn't really seem to do anything just gives me a > and nothing else..
it does it too a lot if I am trying to mount stuff off my external drive which is located on /media/Local\ Disk/

Generally it goes like this /media/Local\ Disk/ (all with tab complete then I type the G to get Games and it goes /media/Local\ Disk/Gamgrep: Trailing Backslash..

What does that even mean??

---

### Post by Mular on 2007-12-14
Ok not 100% sure but I think it has to do with the fact that I am mounting a external USB with NTFS file system..

It didn't seem to do it when I mounted it via sudo ntfs-3g mount..

Now the question is how do I get it to auto do this.. I am assuming I have to edit it in the fslab?

*** cancel that.. did it to me anyway*** blah ;)

---

### Post by Mular on 2007-12-14
too bad you can't uninstall grep ;) But I guess thats just my noobishness sure its a super useful program just annoying what its doing.

---

### Post by llamakc on 2007-12-14
Using the command `ls` post the contents of the directory that HAS the iso you want to mount. Let us see exactly as it is in your terminal. Wrap your cut/paste with the code command in the terminal (the # sign in the editor).

---

### Post by Mular on 2007-12-14
mular@AlphaLinux:~$ ls /media/Local\ Disk/Games/Warcraft\ III/Warcraft\ III\ and\ The\ Frozen\ Throne/
Warcraft III - The Frozen Throne [Disk 1].iso.iso
Warcraft III - The Frozen Throne [Disk2].iso
Warcraft III - The Frozen Throne [Disk3].iso
mular@AlphaLinux:~$ 

If I do sudo mount -o loop /media/Local\ Disk/Game, the tab grep trailing thing will happen when i try to do it on Game.. 

If I do cd as opposed to mount it will get me all the way to the directory the iso's are in.

Then if I do sudo mount War and hit tab it will show me Warcraft III - The Frozen Throne [Disk      --- and if I hit tab then it will do grep trailing backslash...

---

### Post by llamakc on 2007-12-14
```
sudo mount  -o loop "Warcraft III - The Frozen Throne [Disk 1].iso.iso" /path/to/mount
```


What about this? And WHERE are you mounting it to?

---

### Post by annda on 2007-12-14
it seems to be a [reported bug]("https://bugs.launchpad.net/ubuntu/+source/bash/+bug/159874") - please confirm this at launchpad.

i have been able to reproduce it with dummy files with almost similar names and hitting TAB **twice** for ambiguous filenames.

until the bug is fixed, as a workaround you can use the 'ls' command first to find out what you need to type in order to avoid confusing bash - or does it happen after a single TAB? in that case, post the issue on launchpad, please.

---

### Post by Mular on 2007-12-14
yes it does happen with one tab.

Should I make a new bug post or reply to the one there?

---

### Post by annda on 2007-12-14
> **Mular said:**
> yes it does happen with one tab.

Should I make a new bug post or reply to the one there?

i think you should use the existing post to report your problem. please include the exact mount command you have used and the problematic filenames (output of 'ls' in both directories that cause trouble).

thanks. that will help the developers to help us all, so you will actually help us all.

ps. include the bash version too. you can find it out with this command:
```
bash --version
```

---

### Post by Mular on 2007-12-14
Ok its done! Thanks for the help hopefully my post is understandable.. !

---

### Post by moderatelymodest on 2008-01-05
For me the problem seems to be related to sudo. 
If i type in the mount command without sudo it works great and then I just hit Home and type in the sudo.

Guess it has something to do with the special sudo tab completion.

---

