---
title: "Need help with code, please."
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2005-12-23
I'm trying to get my modem set up by following these directions:-

Unpack with
$ tar zxf SLAMR.tar.gz
creating slamr_for_2.6.12-9-386/
$ cd slamr_for_2.6.12-9-386/

Look around
$ ls
There will a README

Define a SITE for the drivers:
SITE=/lib/modules/`uname -r`/extra

so you can do shorthand things like
$ echo $SITE
          /lib/modules/2.6.12-9-386/extra
............................................
Up to this point, everything was going fine.
............................................

............................................
I could not understand how to get this next instruction to work.
............................................

Make a target folder/
$ sudo mkdir $SITE

Copy the drivers there
# sudo cp *.ko $SITE/

check with
# ls $SITE

I would really appreciate some help here.

Thanks.

---

### Post by cstudent on 2005-12-23
Did you try and get errors or are you just curious what it means? Just looking at the code I would think it would work.

---

### Post by L Campbell on 2005-12-23
[QUOTE=cstudent]Did you try and get errors or are you just curious what it means? Just looking at the code I would think it would work.[/QUOTE]

Thanks for your reply.

I was not sure why the '/ ' was in the top line but then I don't know much, anyway.   :-)

Make a target folder/
$ sudo mkdir $SITE

This is what I got:-

lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$ sudo mkdir $SITE
Password:
mkdir: invalid option -- r
Try `mkdir --help' for more information.

lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$ sudo cp *.ko $SITE/
cp: invalid option -- /
Try `cp --help' for more information.

lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$ sudo cp * .ko $SITE/
cp: invalid option -- /

Kind regards.

---

### Post by cstudent on 2005-12-23
[QUOTE=L Campbell]

Define a SITE for the drivers:
SITE=/lib/modules/`uname -r`/extra

so you can do shorthand things like
$ echo $SITE
          /lib/modules/2.6.12-9-386/extra

[/QUOTE]


When you entered the SITE= command, did you put two dashes before the r in uname -r? And was you able to echo $SITE and get something like they suggest?

---

### Post by kabus on 2005-12-23
ignore, my mistake.

---

### Post by L Campbell on 2005-12-23
[QUOTE=cstudent]When you entered the SITE= command, did you put two dashes before the r in uname -r? And was you able to echo $SITE and get something like they suggest?[/QUOTE]

I just found the ' history ' command today, so hopefully I will be able to give a good answer.     :-)

It looks like I put one dash before the ' r '
  
  SITE=/lib/modules/'uname -r'/extra

This is what I got when I tried ' echo '

lcampbell@ubuntulewis:~$ echo $SITE /lib/modules/2.6.12-9-386
/lib/modules/2.6.12-9-386
lcampbell@ubuntulewis:~$

Also, I tried this again.

campbell@ubuntulewis:~$ sudo mkdir $SITE
Password:
mkdir: too few arguments
Try `mkdir --help' for more information.
lcampbell@ubuntulewis:~$ sudo mkdir $SITE/
mkdir: cannot create directory `/': File exists      (I have tried a search and I can't see any files with ' SITE ' that were created in Dec.)
 
I appreciate your continued interest.

---

### Post by cstudent on 2005-12-23
Ok. First off, you are not creating a directory called SITE. SITE is more a varible which will hold the path /lib/modules/2.6.12-9-386/extra. I'm not sure what you're working with, but the 2.6.12-9-386 is referring to a kernel version. Your kernel may be different. Anyway, the echo command should just be:

```


echo $SITE


```

And it should give you /lib/modules/2.6.12-9-386/extra as a response.

Start your process again at the SITE= command and then see what you get with just echo $SITE.

---

### Post by cstudent on 2005-12-23
After going back and re-reading your original post. You could just forget the whole SITE thing and just replace anywhere the instructions want you to use $SITE with /lib/modules/2.6.12-9-386/extra. All this is trying to do is keep you from having to type it over and over, but cut and paste works just as easy. ;)

---

### Post by L Campbell on 2005-12-23
[QUOTE=cstudent]After going back and re-reading your original post. You could just forget the whole SITE thing and just replace anywhere the instructions want you to use $SITE with /lib/modules/2.6.12-9-386/extra. All this is trying to do is keep you from having to type it over and over, but cut and paste works just as easy. ;)[/QUOTE]


Thanks, that sounds like a good idea.

I haven't gone into Ubuntu to try it yet but my instructions go on to say that;

ls $SITE should show slamr.ko slusb.ko ungrabwin-modem.ko

Well it doesn't, it shows files that are in my Home folder.

Anyway, I'll boot up the Ubuntu again and see what happens.

Many thanks.

---

### Post by cstudent on 2005-12-23
One further note. The part of the SITE= command where you see /'uname -r'/ would substitute your current kernel version in it's place. To find out your kernel version you can enter uname -r in a terminal. You would want to use whatever version number the uname command gave you instead of the version number in your example.

---

### Post by L Campbell on 2005-12-23
[QUOTE=cstudent]One further note. The part of the SITE= command where you see /'uname -r'/ would substitute your current kernel version in it's place. To find out your kernel version you can enter uname -r in a terminal. You would want to use whatever version number the uname command gave you instead of the version number in your example.[/QUOTE]

Thanks again.  I believe I'm following your logic here but I'm still having trouble persuing it through to a satifactory conclusion on my computer.

Must be _something_ that I've screwed up along the way.

..............................

lcampbell@ubuntulewis:~$ uname -r
2.6.12-9-386
lcampbell@ubuntulewis:~$ SITE=/lib/modules/'uname -r'/extra
lcampbell@ubuntulewis:~$ echo $SITE
/lib/modules/uname -r/extra
lcampbell@ubuntulewis:~$ sudo mkdir $SITE
Password:
mkdir: invalid option -- r
Try `mkdir --help' for more information.
lcampbell@ubuntulewis:~$ sudo mkdir /lib/modules/2.6.12-9-386/extra
lcampbell@ubuntulewis:~$ sudo cp *.ko /lib/modules/2.6.12-9-386/extra
cp: cannot stat `*.ko': No such file or directory
lcampbell@ubuntulewis:~$ sudo cp * .ko /lib/modules/2.6.12-9-386/extra
cp: omitting directory `Desktop'
cp: omitting directory `Modem'
cp: omitting directory `slamr_for_2.6.12-9-386'
cp: cannot stat `.ko': No such file or directory

.......................................

Kind regards.

---

### Post by cstudent on 2005-12-23
You need to be either in the directory of the files you are trying to copy or add the path before the *.ko

Put yourself in the directory:

```

cd slamr_for_2.6.12-9-386/
sudo cp *.ko /lib/modules/2.6.12-9-386/extra

```

or add the path:

```

sudo cp /slamr_for_2.6.12-9-386/*.ko /lib/modules/2.6.12-9-386/extra

```

---

### Post by L Campbell on 2005-12-23
[QUOTE=cstudent]You need to be either in the directory of the files you are trying to copy or add the path before the *.ko

Put yourself in the directory:

```

cd slamr_for_2.6.12-9-386/
sudo cp *.ko /lib/modules/2.6.12-9-386/extra

```

or add the path:

```

sudo cp /slamr_for_2.6.12-9-386/*.ko /lib/modules/2.6.12-9-386/extra

```[/QUOTE]


Those certainly look like clear and implicit instructions.  Thank you.

Unfortunately, although they were easy enough to follow (I thought) my computer didn't seem to like them.
.................
lcampbell@ubuntulewis:~$ cd slamr_for_2.6.12-9-386/
lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$ sudo cp *.ko /lib/modules/2.6.12-9-386/extra
lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$ SITE=/lib/modules/'uname -r'/extra
lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$ echo $SITE /lib/modules/2.6.12-9-386/extra
/lib/modules/uname -r/extra /lib/modules/2.6.12-9-386/extra
lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$ sudo mkdir $SITE

Am I correct up to this point?

mkdir: invalid option -- r
Try `mkdir --help' for more information.
lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$ sudo cp /slamr_for_2.6.12-9-386/*.ko /lib/modules/2.6.12-9-386?extra
cp: cannot stat `/slamr_for_2.6.12-9-386/*.ko': No such file or directory
lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$
......................

It always seems like the ' mkdir ' is a stumbling block but, if I'm trying to create a place to stash these files, that would be the way to do it.

I apologize if this is boring you.

Kind regards.

---

### Post by cstudent on 2005-12-23
[QUOTE=L Campbell]
lcampbell@ubuntulewis:~$ cd slamr_for_2.6.12-9-386/
lcampbell@ubuntulewis:~/slamr_for_2.6.12-9-386$ sudo cp *.ko /lib/modules/2.6.12-9-386/extra[/QUOTE]

This part is all you should need. Your .ko files should now be in the directory /lib/modules/2.6.12-9-386/extra.

Try entering this command in the terminal and see if you see your .ko files.

```

ls /lib/modules/2.6.12-9-386/extra/

```
That is a lower case LS at the beginning. It means list.

---

### Post by L Campbell on 2005-12-24
[QUOTE=cstudent]This part is all you should need. Your .ko files should now be in the directory /lib/modules/2.6.12-9-386/extra.

Try entering this command in the terminal and see if you see your .ko files.

```

ls /lib/modules/2.6.12-9-386/extra/

```
That is a lower case LS at the beginning. It means list.[/QUOTE]

Thanks very much, that cleared up a mystery for me.

I appreciate your help.

Kind regards.

---

