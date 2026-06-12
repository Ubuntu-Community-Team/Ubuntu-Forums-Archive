---
title: "$HOME/.dmrc ignored?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-12-21
ok, i dont know what caused it, but my account[also known as non-root admin] is being a little [to replace the word i used] <i>difficult</i>. it lets me log on, but brings up a warning box message saying 
```
 User's $HOME/.dmrc file is being ignored. 
This prevents the default session and language from being saved. 
File should be owned by user and have 644 permissions. 
User's $HOME directory must be owned by user and not writable by other users.
```i tried 
```

sudo chown bluefoxx:bluefoxx /home/bluefoxx/.dmrc
chmod 644 '/home/bluefoxx/.dmrc'

```and 
```

sudo chown bluefoxx:bluefoxx "$HOME/.dmrc"
chmod 644 "$HOME/.dmrc"

```but neither has worked
any way to fix this?

---

### Post by nowshining on 2007-12-21
```
File should be owned by user and have 644 permissions. 
User's $HOME directory must be owned by user and not writable by other users.
```

first u left out sudo in front of chmod

and 2

check the permissions on /home/ur username

(filesystem - home - ur username)

press alt + f2 and navigate (left pane) filesystem - home 

right click the folder ur username and select properties and under permissions check and see if anything went wrong and while ur in gui mode u can also enter the username / urs home and press ctrl + h and find that file and right-click - preoperties - permissions and check them out too..

---

### Post by gumpontheweb on 2007-12-22
I think I know how you got this problem. I deleted my user and now when I tried to use the same name again, I get the same message...
Being a TOTAL newbie, I did the only thing I could guess. I re-created my user and changed the "User ID" in the advanced tab of "create a user".
This didn't fix anything!
When I tried to log in, nI got a whole bunch more errors!!!
It did end up brining me to my desktop icons?
What can we do?

---

### Post by p_quarles on 2007-12-22
The easiest way to solve this problem is to simply rename the file. This way, the next time you log in, a new .dmrc will automatically be created with the correct ownership and permissions. This can be accomplished by running the following command:
```
sudo mv /home/*username*/.dmrc /home/*username*/.dmrc.bak
```

---

### Post by MacHaddock on 2007-12-26
This didn't work for me. It changed the name to dmrc.bak but when I reebooted the sytem didn't create a new one.

what  nowshining  said worked though. Thanks

---

### Post by Martje_001 on 2007-12-26
Do this:
```
chmod 644 ~/.dmrc
sudo chown `whoami` /home/`whoami`/.dmrc
sudo chmod 700 /home/`whoami`
```

(`whoami` can be replaced with a username. If you do `whoami` ubuntu will put the user there which is currently logged in)

Edit: If you get 'file does not exists' errors do:
```
touch ~/.dmrc
```

---

### Post by dondad on 2007-12-26
Try this. 
```

To fix file permissions after copying (works on home directory also DAMHIKT)

Navigate to the top file that you want to change along with everything below,

sudo chown -R user:user .

Note the dot

then 

sudo chmod -R u_rwx .

again, note the dot.

(replace user with your username)

```

I got this from another ubuntu thread a few months ago, but I copied it to a file and cannot remember who to give credit to. It has saved me a couple of times with the same problem.

I have found that the usual cause of this error is to use sudo rather than gksudo when launching a graphical application. Sometimes it messes up the permissions.

---

### Post by filstep on 2007-12-28
thanks Martje_001 - it worked for me

---

### Post by 99bluefoxx on 2007-12-30
> **Martje_001 said:**
> Do this:
```
chmod 644 ~/.dmrc
sudo chown `whoami` /home/`whoami`/.dmrc
sudo chmod 700 /home/`whoami`
```

(`whoami` can be replaced with a username. If you do `whoami` ubuntu will put the user there which is currently logged in)

Edit: If you get 'file does not exists' errors do:
```
touch ~/.dmrc
```
thanks, that one worked fine for me, now to get compiz working in gutsy, i think i like fiesty more right now[i wish i could import all apps/settings lol]

---

