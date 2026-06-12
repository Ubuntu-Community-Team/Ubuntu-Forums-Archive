---
title: "resolv.conf"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by mikeymouse on 2006-10-22
How do I save a resolv.conf file in /etc?
 Lets just say i do not understand sudo and i cannot get online in Ubuntu without creating that file.
 I know how to use root in other versions of linux but sudo has me beat.
 Any help would be appreciated.
 thanks  mikeymouse

---

### Post by taurus on 2006-10-22
You can boot your machine with the LiveCD.  Then mount your partition where / is and just copy to it!

---

### Post by CatKiller on 2006-10-22
> **mikeymouse said:**
>  I know how to use root in other versions of linux but sudo has me beat.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

All you need to do is prefix the command that you want to run as root with **sudo**, or **gksudo** for graphical applications. Easy.

So to edit /etc/resolv.conf, you'd use ```
sudo nano /etc/resolv.conf
```

---

### Post by mikeymouse on 2006-10-22
I have created a file 'resolv.conf' and saved it to my home directory.
 What i want to know is how to save this file to /etc using sudo.
 I would appreciate it if you could show me the coding to do this.
 after i type sudo what do i enter to save 'resolv.conf' to the /etc file..
 Sorry if i sound dense, but i do like it when i can log in as root,do what i need to do and then log back out and go as user.
 It all use to seem so easy.
 your help is appreciated.
 thanks mikeymouse

---

### Post by taurus on 2006-10-22
```

sudo cp ~/resolv.conf /etc/resolv.conf

```

---

### Post by dannyboy79 on 2006-10-22
you shouldn't need to create this file yourself! If it's not there it might just go away after you create it and put it in /etc/. do you know if ytou accidentally deleted this file? is that why it's gone? just trying to point out that the resolve.conf file is something created by the system! ubuntu has the 'e' on the end of resolve were as a lot of distros don't. I am pretty sure cause when I looked for it in the past I thought I remembered finding it with the 'e'. I could be wrong but I don't think so. Maybe you think you needed  to create it cause of a thread you read but I am not sure.

---

### Post by taurus on 2006-10-22
What "e" at the end are you talking about?  It has been /etc/resolv.conf and always been /etc/resolv.conf...

```
-rw-r--r-- 1 root root 50 Oct 17 05:56 resolv.conf
```

---

### Post by mikeymouse on 2006-10-22
> **taurus said:**
> ```

sudo cp ~/resolv.conf /etc/resolv.conf

```
  
I used the above coding to try to move the file 'resolv.conf' from my home directory to /etc.
 It did not work, is there any additional code required to add to the above?](*,)

---

### Post by taurus on 2006-10-22
What do you mean it doesn't work?  I assume you log in as a regular user and your new resolv.conf is in your home directory, ~!!!  Did you get any error message when you ran that command?

---

### Post by dbott67 on 2006-10-22
Just edit the existing /etc/resolv.conf file.

Open up the one your created with gedit
```
gedit ~/resolv.conf
``` and then copy the contents of the file to your clipboard (CTRL-A to select all; CTRL-C to copy).  Next, open the system 'resolv.conf' file"
```
sudo gedit /etc/resolv.conf
```

Comment out any existing lines by putting a '#' in front of the line, and then paste (CTRL-V) your content at the bottom.

```

# This is the existing line:
# nameserver 192.168.1.2

# This is the new line
nameserver 192.168.1.1
```

-Dave

---

### Post by mikeymouse on 2006-10-22
> **taurus said:**
> What do you mean it doesn't work?  I assume you log in as a regular user and your new resolv.conf is in your home directory, ~!!!  Did you get any error message when you ran that command?

My file is in my home directory home/harry
the error message is
 'missing destination file operand after 
  sudo cp ~/resolv.conf/etc/resolv.conf'
thanks for your help:

---

### Post by taurus on 2006-10-22
There is a space between ~/resolv.conf and /etc/resolv.conf!!!

---

### Post by mikeymouse on 2006-10-22
> **taurus said:**
> There is a space between ~/resolv.conf and /etc/resolv.conf!!!

 Thankyou all is well, your help is much appreciated.
 Just goes to show you what a little space between (the ears) will do.. :mrgreen:

---

### Post by taurus on 2006-10-22
That's why you want to use the cut 'n paste with the mouse so there won't be any mistake in leaving something out...  ;)

---

### Post by CatKiller on 2006-10-22
> **taurus said:**
> That's why you want to use the cut 'n paste with the mouse so there won't be any mistake in leaving something out...  ;)

And tab-completion for filenames and paths for when you can't cut&paste, for whatever reason.

---

### Post by MNCaudill on 2006-10-22
Sorry for the dupe

---

### Post by MNCaudill on 2006-10-22
Try this at the command line prompt:

> sudo echo "nameserver 208.67.222.222" > /etc/resolv.conf
sudo echo "nameserver 208.67.220.220" >> /etc/resolv.conf

This will point you the OpenDNS server which are very dependable.

---

### Post by dannyboy79 on 2006-10-23
> **taurus said:**
> What "e" at the end are you talking about?  It has been /etc/resolv.conf and always been /etc/resolv.conf...

```
-rw-r--r-- 1 root root 50 Oct 17 05:56 resolv.conf
```

oops, it must have been the other way around. I must have been reading a forum within another distro and it must have been telling me to edit resolve.conf and not resolv.conf. then when I went to find it it wasn't named with the 'e' but ubuntu had it without the 'e'. so i just mixed up was I was trying to inform you of, sorry. also, why aren't you guys asking the main question? why is he trying to make his own resolv.conf file? mine was in /etc/ without having to create one.

---

### Post by randiroo76073 on 2006-10-23
I had to create my own in Kubuntu, it was missing in a fresh install, so no it's not always there, maybe should be, but not to be counted on :)

---

