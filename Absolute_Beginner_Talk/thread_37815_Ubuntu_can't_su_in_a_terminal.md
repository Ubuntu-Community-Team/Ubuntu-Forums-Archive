---
title: "Ubuntu can't su in a terminal"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by dranthu on 2005-05-28
hmm I'm a little perplexed by this problem I'm having
I'm having alot of trouble with the different su, kdesu
commands causing apps to crash or just not working
like I can't use su in a terminal it just refuses to
authenticate the password (even though I've typed it in
correctly)
and does a authentication failure
and half of the time kdesu cause what ever program
I'm starting to crash while loading

---

### Post by dranthu on 2005-05-28
I don't understand whats up with this
I can kdesu with the password I'm using
and sudo
but the su command refuses to authenticate the same password

---

### Post by Kyral on 2005-05-28
I dunno about kdesu, but you can use su in a terminal through sudo su

---

### Post by dranthu on 2005-05-29
really I have to use sudo before su?
I didn't know that
(I've never had a problem with it before)

---

### Post by dranthu on 2005-05-29
hmm Kubuntu won't use the su command period
it always fails to accept my password no matter what
I'm entering
hmm I wonder what is up with it
the thing is nagging me that its here
broken and I don't know how to fix it

---

### Post by tread on 2005-05-29
Just default su will SwitchUser to root .. su will start a different bash shell running as that user. It doesnt run an application as that user .. thats sudo.

so if you want to run as a different user try

su - different user
or 
su different user

I hope I am answering the question correctly .. I didn't understand the problem very correctly.

---

### Post by somuchfortheafter on 2005-05-29
ok here you go
sudo -s
*enter your username password*
passwd
*enter the password you want for su*
now use su and your new root password all your little heart wants....

---

### Post by dranthu on 2005-05-29
sorry I guess I didn't explain very well
I'm trying to use su to switch into my root account
but it refuses my password when I'm entering
the right password

---

### Post by dranthu on 2005-05-29
thanks for the help somuchfortheafter
that works for me
though why can't I just type su
log in just like any other distro?
what you told me to do works
but the default still won't accept
my password

---

### Post by Jenda on 2005-05-29
[QUOTE=dranthu]thanks for the help somuchfortheafter
that works for me
though why can't I just type su
log in just like any other distro?
what you told me to do works
but the default still won't accept
my password[/QUOTE]
 That's because the **sudo **command uses your user's password, whereas the **su **command uses the root pwd, which is not set in Ubuntu by default(read: is set, but nobody to my knowledge will tell you what it is).
So you have to use the **sudo** command, which has root priveledge even though it only uses your pwd, to set the root pwd, and that in turn you can use with the root-exclusive **su** command.
I'd still recommend using **sudo **every time for your work. It's much easier to screw up under **su**.

---

### Post by dranthu on 2005-05-29
thx for the help
I see the bunnies are spreading :)

---

