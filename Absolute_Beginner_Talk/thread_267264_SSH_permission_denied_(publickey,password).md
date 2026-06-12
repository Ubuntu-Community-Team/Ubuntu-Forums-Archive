---
title: "SSH permission denied (publickey,password)"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2006-09-28
Hi all,

i'd like to ssh in to my machine when i'm on school..

So i used PuTTy to ssh, and that worked perfectly :D

But after some fiddling with my pc (don't know what i've done), ssh doesn't work anymore..

I tried reinstalling the ssh-server, but i keep hitting the same wall ](*,) 

this is what i get
```
iarwain@iarwain-desktop:~$ ssh localhost
iarwain@localhost's password:
Permission denied, please try again.
iarwain@localhost's password:
Permission denied, please try again.
iarwain@localhost's password:
Permission denied (publickey,password).

```

Anyone knows what to do?


Iarwain

---

### Post by bswilson on 2006-09-28
> **Iarwain ben-adar said:**
> Hi all,

i'd like to ssh in to my machine when i'm on school..

So i used PuTTy to ssh, and that worked perfectly :D

But after some fiddling with my pc (don't know what i've done), ssh doesn't work anymore..

I tried reinstalling the ssh-server, but i keep hitting the same wall ](*,) 

this is what i get
```
iarwain@iarwain-desktop:~$ ssh localhost
iarwain@localhost's password:
Permission denied, please try again.
iarwain@localhost's password:
Permission denied, please try again.
iarwain@localhost's password:
Permission denied (publickey,password).

```

Anyone knows what to do?

I think you're doing a couple of things wrong.  First, you should try using the system's hostname **instead of** localhost.  Second, try specifying the username (although that's not critical while you're on THAT system, but you want to do this when you try remotely):

```
$ ssh -l iarwain iarwain-desktop
```

If that doesn't work, then try deleting all the cached encryption keys on your client.

```
$ sudo rm -rf ~/.ssh/known_hosts
```

---

### Post by Iarwain ben-adar on 2006-09-28
Hi,
thanks for the reply :D

I tried what you said, but to no avail :(

btw, i used localhost instead of my hostname, because otherwise it is quite confusing wether i'm in ssh, or not :s


Iarwain

---

### Post by Iarwain ben-adar on 2006-09-29
.. and bumping it back to the top :D


Iarwain

---

### Post by Iarwain ben-adar on 2006-09-29
Bumper


Iarwain

---

### Post by Iarwain ben-adar on 2006-10-08
No one knows something?

Still stumped..


Iarwain

---

### Post by wieman01 on 2006-10-08
Have you installed a firewall recently?

---

### Post by wieman01 on 2006-10-08
Plus... You're password is wrong. I think it's as simple as that. The command "ssh localhost" is fine and everything but the system complains that your password is incorrect. Have you changed it recently?

_**[COLOR="Red"]EDIT:[/COLOR]**_
Have just tested it. Same happens on my system when I enter the wrong password 3 times:
> myuser@Alice:~$ ssh localhost
myuser@localhost's password: 
Permission denied, please try again.
myuser@localhost's password: 
Permission denied, please try again.
myuser@localhost's password: 
Permission denied (publickey,password,hostbased).
However, it connects and allows a session once the right password is entered.

---

### Post by Iarwain ben-adar on 2006-10-08
Hi,
thanks for the reply!

No, i haven't installed a firewall,
and i don't think i changed the pass. How can i reset my password?


Iarwain

---

### Post by wieman01 on 2006-10-08
You usually log on to the other computer with a user that exists on both systems. You enter the remote host's (server's) password. To give you an example:

A. Client: user alice; password 123456
B. Server: user alice; password 654321

-> Connection from client system: ssh server; then enter password = 654321

So if you have changed the user's password on the server you need to take that into account when loging on the next time.

---

### Post by Iarwain ben-adar on 2006-10-08
..
Now i lost it..

Tried entering my pass backwards, still the same error.

How can i add/delete a user from ssh?


Iarwain

---

### Post by tideline on 2006-10-08
In a terminal try ps -afx | grep ssh.

If there is no entry in there for ssh try starting it.  

If it is running, try changing that user's password.  Can you log into that machine with any user?  Try setting a password for root, and trying with that user: ssh root@localhost.

Mike

---

### Post by Iarwain ben-adar on 2006-10-08
```
iarwain@iarwain-desktop:~/Desktop$ ps -afx | grep ssh.
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
 4286 ?        Ss     0:00 /usr/sbin/sshd
24292 ?        Ss     0:00          \_ /usr/bin/ssh-agent /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
24293 ?        Ss     0:00          \_ /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
26960 pts/1    S+     0:00      \_ grep ssh.

```

But how do i change a user's password?


Iarwain

---

### Post by wieman01 on 2006-10-08
Ah... My last note may have been a bit confusing. Let me put it this way: What password are you entering when prompted by SSH?

---

### Post by Iarwain ben-adar on 2006-10-08
the pass is 'benjamin' (without the '')

So i tried entering benjamin and also nimajneb (as you said to type it backwards..)


Iarwain

---

### Post by wieman01 on 2006-10-08
I am sorry, the "backwards" thing was just an example of two different password. Was misleading. That's not what I meant.

You have a local user on the server machine, right? Now try this:
> ssh [COLOR="Red"]your_local_user[/COLOR]@localhost
Then press enter and enter the local user's password. [COLOR="Red"]your_local_user[/COLOR] stands for the user on the server PC.

I am assuming that you are testing this on the machine on which the SSH server is running?

---

### Post by Iarwain ben-adar on 2006-10-08
Tried it,
but i'm trying it on the same machine as the server is running..

I tried it from school aswell, and got the same error..


Iarwain


P.S.: how can i check what user's are made for ssh?

---

### Post by wieman01 on 2006-10-08
Can you show us the commands you are using please?

---

### Post by Iarwain ben-adar on 2006-10-08
Here you go
```
iarwain@iarwain-desktop:~/Desktop$ ssh iarwain@localhost
iarwain@localhost's password:
Permission denied, please try again.
iarwain@localhost's password:
Permission denied, please try again.
iarwain@localhost's password:
Permission denied (publickey,password).
iarwain@iarwain-desktop:~/Desktop$     
```


Iarwain

---

### Post by wieman01 on 2006-10-08
Looks ok. Now please do this command and restart the computer:
> sudo rm ~/.ssh/known_hosts
Then try again to log on using your user (= iarwain) password (= benjamin):
> ssh iarwain@localhost

---

### Post by Iarwain ben-adar on 2006-10-08
Did what you told me to,
same error..


Iarwain

---

### Post by wieman01 on 2006-10-08
Went offline... Different timezone here.

One thing strikes me, though. My output says "hostbased":
> Permission denied (publickey,password,**[COLOR="Red"]hostbased[/COLOR]**).
Have you enabled "host authentication"? I think you would have to do that on both the client & the server side (although I am not sure). Can you check the configuration files for such a line?

I think that - if "hostbased" is set to 'false' - you need to authenticate via public/private key which is slightly more complicated than what you are trying to achieve.

Please try to search for it.

---

### Post by Iarwain ben-adar on 2006-10-09
Hi,
no problem, my school just finished :D

So, this is what i found in my /etc/ssh/ssh_config:```
#   HostbasedAuthentication no
```

Is this what you need?
What do i need to change?


Iarwain

---

### Post by wieman01 on 2006-10-09
Please set it to 'yes', then save the file & restart the computer. See how it goes now.

---

### Post by Iarwain ben-adar on 2006-10-09
I set it to yes,
but i still get the same error..


Iarwain

---

### Post by wieman01 on 2006-10-09
Ok, last resort because I am not too familiar with SSH configuration. Could you reinstall it via Synaptic & click "Mark for complete removal" before you do so? This will also eliminate the configuration file that may have been tempered with.

---

### Post by Iarwain ben-adar on 2006-10-10
```
iarwain@iarwain-desktop:/etc/ssh$ ssh iarwain@localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 2e:c9:ce:35:9f:42:c6:3d:db:12:7c:45:dc:aa:12:20.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
iarwain@localhost's password:
Linux iarwain-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Tue Oct 10 15:56:58 2006

```

That solved it :D

Thanks for the help wieman01,
i'm glad it works again :D

Too bad i don't know what went wrong.. but anyways, it's working!

Yay!


Iarwain

---

### Post by wieman01 on 2006-10-10
> **Iarwain ben-adar said:**
> ```
iarwain@iarwain-desktop:/etc/ssh$ ssh iarwain@localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 2e:c9:ce:35:9f:42:c6:3d:db:12:7c:45:dc:aa:12:20.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
iarwain@localhost's password:
Linux iarwain-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Tue Oct 10 15:56:58 2006

```

That solved it :D

Thanks for the help wieman01,
i'm glad it works again :D

Too bad i don't know what went wrong.. but anyways, it's working!
Yeah... Was the last resort as I said. Don't really like this kind of solution because I usually want to understand WHY things don't work, same as you. But since we got stuck, I am glad you could solve it this way. 

See you next time!

---

### Post by dfox8895 on 2007-03-29
I was getting the same error message and got it to work.  When I setup the host and the server I used the same username and password on both.  I believe this is what is causing the problem because without making any other changes I used a user that is not on both and was able to log in.

Wierd

---

### Post by macogw on 2007-03-29
I ssh into my server like this:
ssh [email]maco@hudson.dreamhost.com[/email]

since your comp probably doesn't have a .com, you'd use the IP address

ssh maco@121.343.234.12
for example

the part before @ should be your username

---

