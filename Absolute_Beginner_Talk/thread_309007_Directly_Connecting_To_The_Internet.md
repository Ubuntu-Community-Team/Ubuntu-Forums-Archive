---
title: "Directly Connecting To The Internet"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2006-11-29
Is there a way to connect to the internet without going through Firefox or Evolution?
  On my PC there is an icon. On my Macs, there is Remote Access. Is there a command that will connect me?
   So far, I haven't had any luck connecting. I have followed Linuxant's instruction carefully and have properly configured the system but it doesn't connect. There is no sound from the modem.
  It may be that this dial-up modem is incompatible and will require the soon-to-be-released 2.6.17-10 driver, but a direct connect command might work.
 Thanks

---

### Post by K.Mandla on 2006-11-29
Are you looking for a command to test your connection? You could always

```
ping www.google.com
```to test it. Or you could use the *wget* command, if you want to download a test file. 

Have I misunderstood your question? :-k

---

### Post by Stunt Double on 2006-11-29
I don't want to test the connection, I want to connect before opening my browser. Or does that normally start when Ubuntu loads?

---

### Post by autocrosser on 2006-11-29
Well--two ways come to mind--

1. Wvdial---In a terminal--type wvdial -config
this should get you to wvdial's set-up--
you can then dial-up by just typing wvdial in a terminal--

I use Gnome-PPP which is a graphic frontend for wvdial

2. Menu>System>Networking (if you are using Edgy--similar for Dapper) tic the Modem connection & then Properties--go thru the various tabs in the panel that will come up---

---

### Post by b3tzi on 2006-11-29
You can install the Network Monitor.
It will connect while booting.

---

### Post by Stunt Double on 2006-11-29
How do I install the Network Monitor?

---

### Post by Stunt Double on 2006-11-29
Gnome ppp sets it up but what is the connect command once it is set-up?

---

### Post by Bartender on 2006-11-29
I'm not sure of how Gnome PPP works.  Maybe it's the same thing.  Anyway, if you have Dapper 6.06 (it's gone in 6.10) click on your panel, click on "Add to Panel" and drag the Modem Monitor icon to the panel.  It's a little red phone.  If you've set the dial-up modem correctly in Networking, all you do is right-click on the Modem Monitor icon, left-click "Activate" and the modem dials/connects. 
That's how my USR external works anyway.  It connects to my ISP without starting Firefox or Synaptic first.
Don't know if that helps any...

---

### Post by Stunt Double on 2006-11-29
Unfortunately, I have 6.10 and can't connect to my internet provider. Linuxant said they will soon release a driver specific to 6.10 / 2.6.17-1O. Guess I'll have to wait... 
  I can report that, so far, everything else on the Ubuntu CD works perfectly.

---

