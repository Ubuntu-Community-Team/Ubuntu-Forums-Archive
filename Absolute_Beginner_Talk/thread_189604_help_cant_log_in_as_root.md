---
title: "help cant log in as root"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by :.D.A.N.: on 2006-06-05
never specifyed a password and now it wont let me in!!

:confused: :confused:  im stuck :confused: :confused:

---

### Post by Sutekh on 2006-06-05
In Ubuntu the root account is disabled.

You should read this link on the use of **sudo** to get root privileges

[Ubuntu Wiki - Root and Sudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by hotbrainz on 2006-06-05
What happened?

Did you type in :

Su 

and it asked you for the password?

Enter the password which you used for your username. If that does not work then type in:

sudo passwd

it will ask for a new password.

No worries. Welcome to Ubuntu

---

### Post by :.D.A.N.: on 2006-06-05
wow thanks, thought i was in deep guano then

:D  thank u :KS

---

### Post by Flavian on 2006-06-05
Can someone help me....
If i try to log in as via su and type in the password I get an error response, something like was not able to log in, sorry.
Whereas when I use sudo it works all fine ?

---

### Post by hotbrainz on 2006-06-05
please try:

sudo passwd

you can change the password then and you should be fine after that

---

### Post by gr0kzer0 on 2006-06-05
Ubuntu has an unusual set-up when it comes to the root account.  It is "disabled" by default, and if you want to do something that requires root privileges, the "proper" way to do it is by prefixing the command with "sudo".  You will be prompted for a password: give the password for your main user account, and the command will be executed.

There are ways to activate the root account, if you are so minded. (I did it, just because it annoyed me not being able to log in as root on my own computer). The way I did it was to type in ```
sudo passwd root
```  This enables you to set a password of your choice for the root account.

Really, there isn't much point in doing this.  Since I set a password for the root account, I haven't used it once.  Sudo is quite adequate when you need to do administrative tasks.  But it is annoying, the way Ubuntu tries to stop you logging in as root.  I know there are dangers associated with the use of the root account, but I don't really appreciate Ubuntu's way of dealing with it.  It's rather patronising - can't we be trusted to administrate our own computers properly?

Incidently, once you've activated your root account, you will find that root can't login to the GUI.  This can be changed, I believe, though I haven't bothered myself.  Also, remote login by root is disabled.  This is a wise precaution, and I would advise anyone to  let that alone.

---

