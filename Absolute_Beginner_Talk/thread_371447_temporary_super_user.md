---
title: "temporary super user"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by benner on 2007-02-26
I am trying to change the permissions for a file 

/proc/sys/kernel/shmmax

so that i can execute 

echo "0x7fffffff" > /proc/sys/kernel/shmmax

to try to get cinelerra working.  i'm just following various instructions from posts here and there and ran into the silliest problem that i should know how to do but don't--temporarily give myself root privileges temporarily to change the permissions.  it won't let me unless i am the owner.  i type 'sudo su' into a terminal, type my password and i assumed that i am suddenly a superuser and can do anything as root.  apparently i can't.  i guess i am only root as far as the terminal is concerned.  what if i want to operate in the gui as root so i can do something (like change the permission for a file?  is there a simple command? by the way, if you know anything about cinelerra, let  me know.  there seem to be a lot of dependency problems to get it to run.  thx.

---

### Post by Maestro23 on 2007-02-26
> sudo -i

Gives temp root console: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

*Also a drag & drop sudo(GUI) trick on there towards the bottom.

---

### Post by benner on 2007-02-27
i have logged in as root and using each other login i have.  i still can't change the permission for that file.  each time it says i am not the owner.  any idea?

---

### Post by Adramelech on 2007-02-27
then u r not logged as root.

sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax

should work

---

### Post by benner on 2007-02-27
i had.  this is the response:

bash: /proc/sys/kernel/shmmax: Permission denied

so i tried to locate the file /proc/sys/kernel/shmmax and change the permission for read and write access.  currently even root has only read access.  i guess it is pretty important.  i can't seem to change the permission so that i can write to it.

---

### Post by Adramelech on 2007-02-27
sudo chmod u+w /proc/sys/kernel/shmmax

That will make the owner able to write to the file

---

### Post by benner on 2007-02-27
it appears that root has read and write but the group called 'root' has only read.  when i executed the command

echo "0x7fffffff" > /proc/sys/kernel/shmmax

i didn't get an error so i guess it worked.  i don't really know what it does.  i am trying to get cinelerra to work.  the error is

cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen


and the posts that i read suggested running 

echo "0x7fffffff" > /proc/sys/kernel/shmmax

to solve the problem.  didn't work.  thanks for the help though, folks.  unless someone here knows what i am trying to do, perhaps i should try another post in a different section.  i think cinelerra has a lot of bugs.  i really need a good video editor for linux.  i used sony vegas video for a long time in windows.  since i gave up the [microsoft] habit i haven't fpound a good one.  every problem seems to lead to another one (and something new learned) so thanks again.  (suggestions on a good video editor would also be most welcome)

---

### Post by Adramelech on 2007-02-27
I remember i compiled cinelerra on dapper and it worked. your error is proly cause by a version error on libquicktime.

---

### Post by cdrom600 on 2007-03-09
I was able to run the command "echo "0x7fffffff" > /proc/sys/kernel/shmmax" by getting a root terminal using "sudo -i" and then entering the command.  I'm using Ubuntu Edgy.

---

### Post by mateuszbaranski on 2007-04-12
> **benner said:**
> 
i am trying to get cinelerra to work.  the error is

```
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen
```

and the posts that i read suggested running 
```
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```
to solve the problem.  didn't work.  

I am sure it didn't.

I' ve got the same problem. I installed fresh ubuntu 6.10. Then I installed cinelerra from 
```

deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./

```
It worked. It worked until I agreed to install some security updates (included faad & faac and other video connected packages.). Got the same message about *symbol lookup error*

[FONT="Arial Black"]Solution:[/FONT]

I looked into 
```
/root/.synaptic/log
```
(must be root to change directory)
- there is a log for every installation by synaptic there. I found the log from the day on which synaptic has changed mentioned packages (faac, faad etc.)

Then I forced synaptic to change the version of those packages back to version before the bloody update had happened.
The one which was causing troubles was:
**libfaad2-0**

Good luck.

---

### Post by tubunu on 2007-06-27
Then I forced synaptic to change the version of those packages back to version before the bloody update had happened.
The one which was causing troubles was:
**libfaad2-0**

Good luck.[/QUOTE]

How did you go about that? Could you please post an example, thank you.

---

