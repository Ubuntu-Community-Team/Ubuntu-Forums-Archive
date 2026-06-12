---
title: "How would I go about using SSH?"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by TomX on 2005-10-29
Hey,

I have two computers, one for me, one for my family.

I am running Gentoo and my family are running Ubuntu, however, since they are hardly computer literate I have to manage their computer. I plan to do this, once the network has been setup, through an SSH connection.

I plan to SSH their root account so I can do whatever I need to do, however, I know Ubuntu has a thing about not promoting using the root account through use of sudo. So, given this, how do you promise I manage the computer?

1. Create a user account with a lot of root access (i.e. so I'd have to use sudo) for myself;
2. Enable the root account and be careful (however, would this be a security problem if connected to the internet?);
3. Other?

Thanks in Advance
Tom

Also, do you think, given that my family are moderately computer literate, I should given them sudo access to Synaptic or is it too risky (incase they remove a vital app or install "wrong" apps)?

---

### Post by adwait on 2005-10-29
Regardless of which account you are logged in to on a machine, you can ssh into another machine by using 
```
ssh -l root
```
In ubuntu, you can enable the root account using
```
sudo passwd
```

Also, you can just SSH to Ubuntu with a user who has sudo permissions, and then use sudo. To give sudo permissions to a user, use
```
visudo (as root or with sudo)
```
And add a line like
> username ALL = (ALL) ALL


---

