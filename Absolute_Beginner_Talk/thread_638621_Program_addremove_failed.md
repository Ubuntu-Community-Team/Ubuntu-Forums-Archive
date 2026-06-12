---
title: "Program add/remove failed"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by calandrensis on 2007-12-12
Hello there,
I am a total beginner in Ubuntu and, obviously, I need your help. Please, excuse my litteral poverty, since I am not an American, but a Hellene.
So, the Program add/remove command from the Applications menu can't work. When I try to make it start, this is the output:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

As far as I have understood, /etc/apt/sources.list denies access to me.

PLS, help!
[RIGHT]Georgios[/RIGHT]

---

### Post by rockinlinux on 2007-12-12
i have never had this problem but i think you need to go into the synaptic package manager (located in the system menu under admin) and yo should be able to fix your broken packages there.

---

### Post by calandrensis on 2007-12-12
Thanks for your reply.

Yes, I did.
It was a dansguardian beta that was destroyed. I totally uninstall it, but nothing went better. Program add/remove produces the same answer.

How could I possibly take access over the sources.list file?

---

### Post by Sef on 2007-12-12
> Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

1) Go to synaptic:  System > Administration > Synaptic Package Manager

2) check if Add/Remove is working ok.

a) If yes, then download what you want.

b) If no, then continue to step 3

3) Applications > Accessories > Terminal

then copy and paste this code:  ```
gksudo gedit /etc/apt/sources.list
```

4) Then wait for a reply.  

5) If your list is ok or needs a minor fix, then open the terminal again and type in these codes:

a) ```
sudo apt-get update
```

b) ```
sudo apt-get install -f
```

6) That should fix your problem.  If it doesn't, please let us know and there is more you can do.

---

### Post by Sef on 2007-12-12
> How could I possibly take access over the sources.list file?

It could have corrupted your sources list.  Hopefully the fix above will resolve your problems.

---

### Post by calandrensis on 2007-12-12
Many thanks for your interest.

So, I have already tried these commands, but the result is the same. It 's a problem I have a greek installation of Ubuntu, but these commands output many lines.
The reply for sudo apt-get update ends like this:

Package lists reading... completed
E: Some files were not downloaded, ignored or older ones were used in their place.

The reply for sudo apt-get install -f is similar to this:

Package lists reading... completed
Dependences Tree Constructing
Reading state information... completed
0 upgraded, 0 new installed, 0 will be removed and 19 do not upgrade.

I wait for your further help

---

### Post by shae on 2007-12-12
Post the output from terminal of the following command:
```
cat /etc/apt/sources.list
```

---

