---
title: "No such file or directory?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by wink on 2007-06-27
Trying my hand at using the terminal I was surprised to get the response to **cd** as shown below:

> lutz@lutz2:~$ ls
Desktop  Downloads  Examples  
lutz@lutz2:~$ cd /downloads
bash: cd: /downloads: No such file or directory
lutz@lutz2:~$ cd /examples
bash: cd: /examples: No such file or directory
lutz@lutz2:~$ 

Since **ls** listed my 3 directories, why does **bash** insist that they don't exist? 

Now I am not only a newbie but a befuddled one at that.

Thanks in advance if you can help to unbefuddle me. 

wink

---

### Post by Phixion on 2007-06-27
you need to use:

```

cd Downloads

```

Note the capital D in the dir name :)

---

### Post by santy_kushwaha on 2007-06-27
its simple boy bcoz u are using small letter whereas the file name start with the capital letter so make sure u type excalty what is written or just copy and paste that will help too

---

### Post by Phixion on 2007-06-27
the easiest thing to do whilst browsing directories with console is use TAB alot, it autocompletes and also lists the directories/files that match the text you have already entered.

---

### Post by use a name on 2007-06-27
Also remove the leading / from your commands. You are in your home dir and adding the / tries to enter a folder in the root of the filesystem.

---

### Post by wink on 2007-06-27
Thanks for your replies, especially the last one re using TAB. 

I really do appreciate all the help that is so freely given by so many here. 

P.S. I guess the / is only needed when going into the root dir, right?

---

### Post by lazyart on 2007-06-27
using / tells linux to look from the root to find the directory you specify (just like windows does).

using ~ tells linus to start looking from your home directory.

so, if your username is wink, and you are at /home, the three statements:

cd wink/Desktop
cd ~/Desktop
cd /home/wink/Desktop

take you to the same place.

/ and ~ are absolute references.  Without either, it is a relative reference (relative to where you are in the directory tree).

---

