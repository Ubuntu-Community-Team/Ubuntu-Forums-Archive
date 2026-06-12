---
title: "Pidgin, XMPP&lt; and Guifications...."
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by OZFive on 2008-02-18
I have an issue here.  I need some advice.  I have Pidgin running and installed Guifinotifications.  On XMPP it works kind of wonky.  It gives me 2 to 4 notifications for those individuals when each person comes online and goes offline.  See?

 [IMG]http://img190.imagevenue.com/loc210/th_55144_Pidgin_122_210lo.jpg[/IMG]

I have tried the Pidgin-Libnotify as well and it has the same results.

Any suggestions?

---

### Post by paultag on 2008-02-18
check how many instances of the lnotfy daemon are running.

```

 ps -ef | grep notification-daemon | grep -v grep

```

Failing that, I wrote a Command Line interface to the libntofy daemon, and you can put a single message through, and see how many pop up ( pidgin issue or Daemon issue )


Cheers,
Tag

---

### Post by OZFive on 2008-02-18
Okay I did that and this is my results....

> matthew   5313     1  0 09:09 ?        00:00:04 /usr/lib/notification-daemon/notification-daemon

 [[IMG]http://img42.imagevenue.com/loc790/th_66042_Terminal_122_790lo.jpg[/IMG]](http://img42.imagevenue.com/img.php?image=66042_Terminal_122_790lo.jpg)

---

### Post by paultag on 2008-02-18
humm, so only one copy of the daemon is running.

Give my app a shot, its called Qube.

You can compile it from source like this:

```

sudo aptitude install libnotify-dev bzr
bzr branch http://bazaar.launchpad.net/~qube-dev/qube/qube-dev
cd qube-dev/
./compile.sh
./qube -i "Alert:" "This is a Test"

```

Be sure to check out the source ( just to make sure its not malicious, after all anyone can post code on the web )

Let me know how many alerts come up.

Cheers,
Tag

---

### Post by OZFive on 2008-02-19
Okay well I got the first command done and ran into this....

> matthew@Umbuntu:~$ bzr branch [http://bazaar.launchpad.net/~qube-dev/qube/qube-dev](http://bazaar.launchpad.net/~qube-dev/qube/qube-dev)
bzr: ERROR: Unknown branch format: 'Bazaar pack repository format 1 (needs bzr 0.92)\n'


I do have bzr installed but is says v0.90 in Synaptic.. How and where do I get v0.92?

---

### Post by paultag on 2008-02-19
I believe that 9.2 is in the backports, you might have to enable that source.

Cheers,
Tag

---

### Post by OZFive on 2008-02-19
Well I got the backports open and Dl'ed the newest version and got this....

> matthew@Umbuntu:~$ bzr branch [http://bazaar.launchpad.net/~qube-dev/qube/qube-dev](http://bazaar.launchpad.net/~qube-dev/qube/qube-dev)

Branched 16 revision(s).          

Then I went ahread for this....

> matthew@Umbuntu:~$ cd qube-dev/
matthew@Umbuntu:~/qube-dev$ ./compile.sh
./compile.sh: line 2: g++: command not found


Did I miss a step or do somethin wrong?

---

### Post by paultag on 2008-02-19
sorry bout that, try installing g++

sudo aptitude install g++


Cheers,
Tag

---

### Post by OZFive on 2008-02-20
Well okay, I got that done and did all this....

> matthew@Umbuntu:~$ cd qube-dev/
matthew@Umbuntu:~/qube-dev$ ./compile.sh
matthew@Umbuntu:~/qube-dev$ ./qube -i "Alert:" "This is a Test"
matthew@Umbuntu:~/qube-dev$ 

And I got 1 test message.  So I will have to wait to have someone come online in XMPP and see if my issue is resolved.  I will let you know.

---

### Post by paultag on 2008-02-20
> **OZFive said:**
> Well okay, I got that done and did all this....



And I got 1 test message.  So I will have to wait to have someone come online in XMPP and see if my issue is resolved.  I will let you know.

Yessir, this is officaly a Pidgin / XMPP issue

Let us know,

Cheers,
Tag

---

### Post by OZFive on 2008-02-20
Sorry to report that this had no effect on the issue.  I am still getting the multiple messages when someone logs on and off of XMPP.

---

### Post by OZFive on 2008-02-21
> **paultag said:**
> Yessir, this is officaly a Pidgin / XMPP issue

Let us know,

Cheers,
Tag

IS there any Pidgin Developers here that I can contact about this or just go to their website?

---

