---
title: "questions in my progress to penquinisim"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by at0mic on 2007-01-03
Hi,

Few questions that came up during my progress of building a www server:

1. whats the key command to stop a process like a continuous ping?

2. whats the point of sudo'ing everything when the password is the same one as the user and password you created during installation? should you change the root/sudo password? whats the command to do this if this is the case?

3. whats the kernellog do and is it important. It fails to start on bootup with "unable to start klogd permission denied"

Thanks

---

### Post by Dmole on 2007-01-03
1. kill (type 'man kill' for info)
2. just so you know you or some app is doing somthing system critical (vista now has the same thing)
3. not sure about that

---

### Post by meng on 2007-01-03
1. ctrl-c is the quickest way
2. there are basically two options here a) sudo in front of each individual command OR b) log in as root (or sudo -s) and perform several commands serially. I like a) because I won't get into a situation where I mistakenly perform other commands with root privileges when I didn't want to do that.
3. sorry, I'm ignorant

---

### Post by lloyd_b on 2007-01-03
> 1. whats the key command to stop a process like a continuous ping?

Try  <CTRL> + C.  This will stop any well-behaved console app. Misbehaving apps can be stopped via a "kill -15 <PID>" or "kill -9 <PID>" from another terminal window.

> 2. whats the point of sudo'ing everything when the password is the same one as the user and password you created during installation? should you change the root/sudo password? whats the command to do this if this is the case?

The point is that you log in and do most of your work as a regular user, rather than logging in and working as root.  There are tons of ways to trick a user into running a malicious command, but if the user in question isn't root, then the amount of damage from such tricks is particularly limited.

It also helps in situations where you leave the computer logged-in and walk away - somebody walking up to the computer can mess with the user account, but without that password can't do the same amount of damage that would be possible if it were logged in as root.

> 3. whats the kernellog do and is it important. It fails to start on bootup with "unable to start klogd permission denied"

The kernel log takes messages that would otherwise be sent to the console, and stores them in a more permanent form.  I would suggest reposting that question separately - there is definitely something wrong if the system can start klogd!!!

Lloyd B.

---

### Post by at0mic on 2007-01-03
thnx guys.

one more noob question. how do you search from command line like windows dir /s *.exe

---

### Post by Dmole on 2007-01-03
find -name *something*
DIR is:
ls -al

---

