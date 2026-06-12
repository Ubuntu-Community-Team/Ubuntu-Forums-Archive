---
title: "How to open KDE dektop via ssh?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by AchimRS on 2007-10-02
Hi,
I'm not an Linux expert, so maybe this question is very stupid, that's why I raise it in the beginners talk :-)

Starting dedicated applications via ssh from another computer works with "ssh -X user@computer" and e.g. konqueror. But I would like to see the complete KDE desktop of by KUbuntu Feisty on anoter computer.
Don't misunderstand it, it should not be a remote control of the session seen on the computers display (like done e.g. with vnc) it shoud be a new session running in parallel by a different person.

I already tried to start "kdesktop" but simply nothing happend. The processes are started ad the ssh server and on the client appear some errors from KIOConnection.

How can I start a complete KDE desktop on a remote machine?

Thanks a lot
  Achim

---

### Post by bodhi.zazen on 2007-10-02
Yes you can ...

xinit -e ssh -XCfT user@server startkde -- :1

This will start kde on Ctrl-Alt-F8

Your main desktop will be on Ctrl-Alt-F7 (if you are not running X you can change :1 to :0 , which will then be Ctrl-Alt-F7 )

An alternate is to ssh -X and then forward the kicker :

```
kicker &
```

---

### Post by AchimRS on 2007-10-02
Thanks for the fast response!
> xinit -e ssh -XCfT user@server startkde -- :1
is it true, that this is needed to be started under admin right's, so with "sudo"?

> This will start kde on Ctrl-Alt-F8
>
> Your main desktop will be on Ctrl-Alt-F7 (if you are not running X you can 
> change :1 to :0 , which will then be Ctrl-Alt-F7 )
Buuuh, so this is not very stable on my computer. Basically it works (once), but even if I try it completly locally e.g. with "sudo xinit -e konqueror -- :1" it ends soon with the message "RADEON(0): OK. leaving now..." and do not allow me to switch between the both displaye with Ctrl-Alt-F7/F8

A local "sudo xinit -e startkde -- :1" was never finished completly.

> An alternate is to ssh -X and then forward the kicker :
Hmm, I don't know whether I understood it correctly: I opend an "ssh -X user@computer" and then fired on the remote shell a command "kicker&"
--> this had a very funny behaviour: It slowly shifted my windows on the desktop to the top, only the background is left. But no other desktop appeared..

Thanks so far
  Achim

---

### Post by bodhi.zazen on 2007-10-02
You do not need to use sudo with that command.

kicker will start the kde kicker, or menu, without managing the desktop (ie background).

Not sure about the stability problem ???

---

### Post by AchimRS on 2007-10-03
OK, with help of the following [thread]("http://ubuntuforums.org/showthread.php?t=193079") I was able to start xinit. Now the local "xinit -e startkde -- :1" was successful and stable and I could switch to this session via Ctrl-Alt-F9 and back via Ctrl-Alt-F7.
When I try to do a "xinit -e ssh -XCfT user@server startkde -- :1" as proposed, I will not come very far. The new x-server is started and opens a console which asks for the remote password. After entering the right one, the X-server immediatelly closes :-(
But a "xinit -e ssh -XCT user@server startkde -- :1" works!!!! After looking more in detail to the ssh parameters I found out that this is worth a try, and is was succesful :-)

As you mentioned above, a "ssh -X user@server" with an "kicker" is now working as well. I don't knw what caused the funny behaviour yesterday, but today it works. Both, a "kicker" and "kicker&" works and start an addition KDE-panel on the bottom screen border. I feel this is very confusing, to have two KDE-panels there - it is not simple to decide which one is the local and which the remote (Specially because the open application from the local computer a re shown in the remote KDE-panel as well).

Thanks a lot for the help
  Achim

---

