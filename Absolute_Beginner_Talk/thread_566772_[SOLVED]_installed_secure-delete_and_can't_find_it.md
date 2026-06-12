---
title: "[SOLVED] installed secure-delete and can't find it."
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by axamax on 2007-10-03
I installed secure-delete today (as an equivalent to Eraser program I use on XP) It is listed in Synaptic, I have found files in usr/share/doc  but can't find how to start the program. It doesn't appear in any menu. It doesn't appear in xfce appfinder. I've also tried reinstalled it

Any ideas

---

### Post by llamakc on 2007-10-03
You can see every file that was installed with that package by opening a terminal and typing:

dpkg -L nameofpackage

I'm unfamiliar with XFCE but is there a way to regenerate or refresh the menus?

---

### Post by Ripfox on 2007-10-03
Is it perhaps a command line program i.e.

cd to the file then:

secure-delete (file name here)

---

### Post by Ripfox on 2007-10-03
Bump this...I want to know how to use this too.

---

### Post by axamax on 2007-10-03
> **llamakc said:**
> You can see every file that was installed with that package by opening a terminal and typing:

dpkg -L nameofpackage

I'm unfamiliar with XFCE but is there a way to regenerate or refresh the menus?

This has helped slightly but I need to know which file will start the program and how to add it to a menu
I've attached a screenshot of the terminal window

---

### Post by Munkster on 2007-10-04
Secure-Delete is a collection of 4 Command line utilities. These are:

srm - secure deletion of files.
sfill -  secure overwriting of the unused diskspace on the harddisk.
sswap - secure overwriting and cleaning of the swap filesystem. (note sswap was only tested on linux so far and  you must unmount your swap first!)
smem - secure overwriting of unused memory (RAM)

So if you wanted to securely delete all the files in your Trash bin for example, open a terminal and input

```
$srm -vr /home/<username>/.Trash
```

The switches -v and -r are verbose mode and recursive mode respectively. So it will show the progress of the deletions and will remove any directories and their contents.

If you do not have write permissions though it will not delete the files. This can be overcome by putting sudo in front of the command, but you need to be VERY CAREFUL as it will delete everything and could potentially cripple your system depending on the targets

If you look in /usr/share/doc/secure-delete there is a Read Me file in a gzip called README.gz which explains the full options.

Someone should produce a GUI for this.

---

### Post by Ripfox on 2007-10-05
I second the GUI motion!

---

### Post by Ripfox on 2007-10-05
So my main drive is sda1...what would be the command for cleaning unused space then?

---

### Post by Ripfox on 2007-10-05
bump

---

### Post by Munkster on 2007-10-05
> **ripfox said:**
> So my main drive is sda1...what would be the command for cleaning unused space then?
I don't see the value in overwriting the whole drive or partition, surely any 'sensitive'  ;) data would be on your /home/<username> partition?

In which case it would be the 'sfill' command you will need; the various switches will define how secure the deletion is, it all depends on how paranoid you are.

For example. To wipe all the free space on your home partition with 38 passes,and to see the progress, open a terminal window and enter:

```
sfill -v /home/<username>
```

To reduce the time taken, but lower the security, enter:

```
sfill -vll /home/<username>
```

The more passes, the longer it will take. Check  the ReadME file I mentioned earlier for more guidance though. I'd hate for you to mess up your PC based on something I suggested.

---

### Post by evets on 2007-10-05
Munkster

I read, with interest, this post and your response. It helped, Thank you.
I'm a n00b, and I am having troubles identifying the excecutables. How (enter random cuss words here) do I know which file is the one to click on??? :)

Thanks.

---

### Post by Ripfox on 2007-10-06
Thanks for the explanation.

---

