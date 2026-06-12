---
title: "Quick Noob Terminal Question!"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-03
So I am finally learning how to do stuff in terminal. It's a lot of fun. :)


My question is: Is there a way to delete whole directories or all the files in the in the directory without having to delete each individual file?

Thanks!!

---

### Post by metalpancake on 2008-01-03
yea, you can use sudo rm. make sure you know what you are deleting though.

---

### Post by reckless2k2 on 2008-01-03
be very careful but here's the command;
```

sudo rm -rf thedirectory
```

---

### Post by metalpancake on 2008-01-03
Have a look at this :[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=r/rm]("http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=r/rm")

---

### Post by RomeReactor on 2008-01-03
Hi. Let's say you have a folder named **MyPictures** in your home directory and you want to delete it, icluding the files inside; you do the following:
```
rm -R ~/MyPictures
```
The dash is shorthand for your home directory; the -R option (or -r) tells rm to remove recursively, that is to remove all that is inside, and if inside there are more folders and these folders contain more files *and* folders, it will remove those also.

If you want to use it in your home directory, there's no need to use sudo. Be very careful when running rm -R--with administrator privileges or not.

---

### Post by dwhitney67 on 2008-01-03
There is.

Just like in DOS, you can use a wildcard '*' character, however misuse of the remove command can upset your day if you remove more than you intended.

The command to remove a file (for which you have permissions to remove) is:

```
rm filename
```
or to be prompted if you really want to remove a file:
```
rm -i filename
```
or to remove a file with "extreme prejudice":
```
rm -f filename
```

A wild-card can be used if you wish to remove all or a group of files.  For instance:

```
rm *.txt
```

To remove directories, you will first need to remove the contents of such.  Thus it is necessary to specify the '-r' option with the remove command, thus instructing the remove command to work recursively into the directory.  For example:

```
rm -r dir
```

Be very careful with any and all of the commands above.  Deleting something that the system requires may require you to have to reinstall the OS and/or may lead you to lose important data.  So be warned!

---

### Post by 449 on 2008-01-03
Thanks for the very quick responses guys! Is there anyway to make is ask me yes or no if I want to delete it in my .bashrc file? I already have it so it does ask for individual files.

---

### Post by 449 on 2008-01-03
Oh, and this is completely off topic ,but is there a way to hide all the files with a '.' in front of them in just my home folder?

---

### Post by dwhitney67 on 2008-01-03
> **449 said:**
> Oh, and this is completely off topic ,but is there a way to hide all the files with a '.' in front of them in just my home folder?

This is not practical because some applications may need to create a hidden file in your current working directory.  Normally you should not see files with a preceeding '.' in the name, unless you specifically ask to see them.  If you are using the Gnome file-browser, go into the preferences to indicate that you do _not_ want these files displayed.

---

### Post by dwhitney67 on 2008-01-03
> **449 said:**
> Thanks for the very quick responses guys! Is there anyway to make is ask me yes or no if I want to delete it in my .bashrc file? I already have it so it does ask for individual files.

Insert this into your .bashrc file:

```
alias rm='/bin/rm -i'
```

---

### Post by h4mx0r on 2008-01-10
rm -i is overrided by rm -f though. Also never use rm at all as root without cd to the directory then maybe pwd to check that your there otherwise even if you know what your doing you might rm -r /

---

