---
title: "Can anyone help me with beginner scripting?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-01-03
Here's my script:

```

#
# Script for fcron to connect to ssh and update ip info
#
(date && ifconfig) > foo.txt
ssh joesmith1234@random_ssh.com
#asked for password... how do I enter it?
#copy/replace over foo.txt
rm foo.txt

```

When I am asked for the password, I'm not sure how to get it into the shell...  if I type it directly, it doesn't get recognized by the ssh server...

---

### Post by tszanon on 2008-01-03
> **joesmith1234 said:**
> Here's my script:

```

#
# Script for fcron to connect to ssh and update ip info
#
(date && ifconfig) > foo.txt
ssh joesmith1234@random_ssh.com
#asked for password... how do I enter it?
#copy/replace over foo.txt
rm foo.txt

```

When I am asked for the password, I'm not sure how to get it into the shell...  if I type it directly, it doesn't get recognized by the ssh server...
As far as I know, batch scripts are no good for tasks that require user input (like typing passwords). Unless you can specify the password in the command line (just like you can with sudo) and tell the program to execute a list of pre-determined steps in a text file, I guess you're out of luck.

If I'm wrong, someone please correct me.

---

### Post by joesmith1234 on 2008-01-03
> **tszanon said:**
> As far as I know, batch scripts are no good for tasks that require user input (like typing passwords). Unless you can specify the password in the command line (just like you can with sudo) and tell the program to execute a list of pre-determined steps in a text file, I guess you're out of luck.

If I'm wrong, someone please correct me.

Hmm, do you have any suggestions other than batch scripts, or am I SOL?

---

### Post by joesmith1234 on 2008-01-03
hey, what if I make a .cpp executable, and then use the system() command...?

---

### Post by joesmith1234 on 2008-01-03
hmm, the package "keychain" looks like it might do the trick.  I will try it out.

---

### Post by Xavieran on 2008-01-03
Why don't you use python...it's great for scripting and you can run system commands through it also

---

### Post by joesmith1234 on 2008-01-03
> **Xavieran said:**
> Why don't you use python...it's great for scripting and you can run system commands through it also

Will I have the same problem of not being able to type in the ssh password automagically?

---

### Post by Xavieran on 2008-01-03
Not that I know of...
Can you comment your script so I can write a pseudo python version?

---

### Post by joesmith1234 on 2008-01-03
> **Xavieran said:**
> Not that I know of...
Can you comment your script so I can write a pseudo python version?

```

#
# Script for fcron to connect to ssh and update ip info
#
(date && ifconfig) > foo.txt
ssh joesmith1234@random_ssh.com
#enter password foobar
#copy or replace over foo.txt to the current directory
#close ssh connection
rm foo.txt

```

Like so.

---

### Post by Xavieran on 2008-01-03
#Python version
# Script for fcron to connect to ssh and update ip info
#Import required modules
import os
os.system("(date && ifconfig) > foo.txt")
os.system("ssh [email]joesmith1234@random_ssh.com[/email]")
os.system("rm foo.txt")

I haven't tested this but it should work...as you can see it simply uses the os modules sytem function to execute system commands...
To learn more about python programming/scripting check out [LaRoza's Wiki]("http://laroza.pbwiki.com/"):) thanks LaRoza!
Their probably is a more pure python way to do this,but from what I see ssh doesn't allow you to append a password as an option...

---

### Post by hyper_ch on 2008-01-03
if you run that shell script from the terminal it should ask for user password. Are you using KDE? In Xfce and Gnome it would also prompt you to enter the password.

---

### Post by scorp123 on 2008-01-03
> **joesmith1234 said:**
>   When I am asked for the password ... Why not configure password-less SSH login? It's not that hard. And then your SSH sequence there would work without asking you for a password; authentication is done via cryptographic keys instead.

[https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30](https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30)

---

### Post by svalding on 2008-01-03
The person above me beat me to the answer. Using password-less key based authentication with SSH you will be able to run your script how you want it without any user input whatsoever. Nice, easy, and great for remote network monitoring with Nagios ;-)

---

### Post by joesmith1234 on 2008-01-03
> **scorp123 said:**
> Why not configure password-less SSH login? It's not that hard. And then your SSH sequence there would work without asking you for a password; authentication is done via cryptographic keys instead.

[https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30](https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30)

Does this work even if I don't have admin access to the ssh-server?

---

### Post by scorp123 on 2008-01-03
> **joesmith1234 said:**
> Does this work even if I don't have admin access to the ssh-server? Unless the admin disabled key-based authentication in the "sshd" configuration (that would be bad!) it should work "out of the box" (the options are there in the default configuration!), you just need a valid login on both sides. And you don't even have to generate keys for both sides, in your case it's probably enough if only one account can login without a password (and not vice versa!).

---

