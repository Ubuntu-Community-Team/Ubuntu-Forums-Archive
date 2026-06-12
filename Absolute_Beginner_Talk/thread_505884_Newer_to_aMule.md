---
title: "Newer to aMule"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by moonhost on 2007-07-20
I am going to use aMule GUI, but I do not how to set up. Please let me know what I should putin:

Connect to : XXXXXXXXXXX   port: XXXXX
User name: XXXXXXXXXX
password:  XXXXXXXXXXXXXX

---

### Post by por100pre1 on 2007-07-20
Are you trying to use the aMule daemon? I think you'll do better removing the aMule GUI and using **aMule** instead:
```


sudo apt-get remove amule-utils-gui && sudo aptitude install amule


```
aMule works pretty much like eMule, the aMule daemon works more like a server.

---

### Post by C.S.Cameron on 2007-07-20
Yeh, just use amule. Pretty close to eMule, but seems faster.
Connects easier the first time.
Cork

---

### Post by quattroman on 2007-07-23
I can't connect to aMule. I installed. Opened the ports, but when I hit connect nothing happens.
I know I am missing something. Just don't know what.

---

### Post by family on 2007-07-25
Edit: Why not just torrent?

---

### Post by cooney on 2007-07-29
I (think) I have the same problem too.  I was able, many moons ago, to get 'Limewire' working on FC4.  However, after installing Feisty, downloading amule via 'synaptic',  opening the appropriate ports on my router/firewall and trying to fill in the blanks (amule settings); I still can't get "connected".  :confused:

What are we missing?  Is there a 'howto' somewhere that I'ved missed?  I've searched and searched (googled etc...) and cannot find an answer.  

Maybe it's the full moon?

Just a link please... :popcorn:

:o:o:o

---

### Post by cooney on 2007-07-29
OOPS!!

Sorry for the dupe.    :redface: 

I (think) I have the same problem too.  I was able, many moons ago, to get 'Limewire' working on FC4.  However, after installing Feisty, downloading amule via 'synaptic',  opening the appropriate ports on my router/firewall and trying to fill in the blanks (amule settings); I still can't get "connected".  :confused:

What are we missing?  Is there a 'howto' somewhere that I'ved missed?  I've searched and searched (googled etc...) and cannot find an answer.  

Maybe it's the full moon?

Just a link please... :popcorn:

:o:o:o

---

### Post by testube_babies on 2007-07-29
Do you have servers in your server.met file?

Close aMule, wget this functioning server.met, then start aMule again:
```
cd ~/.aMule
rm server.met
wget --no-check-certificate http://mywebspace.wisc.edu/kpolicano/web/server.met
```

---

### Post by cooney on 2007-07-29
Hi 'Frank Z'. 'testube_babies'

Thanx for the ultra-fast reply.  :)

I guess I don't. re: 'server.met'

I was working on my avatar while waiting for a response.

I will respond to this thread with the results after I do what you suggested regarding 'server.met'.


Thanx again for the fast response,

Bob

---

### Post by cooney on 2007-07-29
Thanx dude (testube_babie),

I think that did it!  If I have any other probs I'll respond.  Otherwise, consider my probelm solved.

Bob

---

### Post by cooney on 2007-07-29
Problem solved!

thanx mate!

bob

---

### Post by brucewagner on 2008-01-14
> **testube_babies said:**
> Close aMule, wget this functioning server.met, then start aMule again

I had the same problem.  Your solution worked perfectly.

(1)  Thanks so much, testube_babies.

(2)  Any word on the aMule people implementing this fix into their standard build included with Ubuntu's Applications-->Add/Remove...?

---

### Post by scrag on 2008-01-14
thank you for the help in how to download a server list to amule, which seemed to work, however when i go to connect it says that their is no valid servers to connect too however the list has since populated since i updated from the terminal. Also somtimes it will connect and then disconnect right after connecting. I`m fairly new to the world of linux and have no idea what else i can do. Any help is greatly appreciated.

---

### Post by Hallvor on 2008-01-15
You should add a few servers manually. Secondly, you should add these servers to your static serverlist by right clicking. Thirdly, under Preferences -> Servers, select connect to static servers only, and untick the "update serverlist" options. That way, you will have a few reliable servers and that is all you need.

For more info, check my signature.

---

### Post by scrag on 2008-01-15
thank you for the quick reply I have followed the steps in your post and am now waiting to see if amule will connect to one of the 6 servers I have set as static
Thanks again I am now connected.

---

### Post by BurningIceBear on 2008-01-26
Hello people.

Im very new to ubuntu and linux, and im still working on my skills :)

I get this line when i enter the code in a terminal window

```
 root@tulkas-desktop:~# cd ~/.aMule
-bash: cd ~/.aMule: No such file or directory

```

I do have installed amule from the add\remove program, so the directory should be on my computer. Can you guys try to help me out?

-The burned Ice bear

---

