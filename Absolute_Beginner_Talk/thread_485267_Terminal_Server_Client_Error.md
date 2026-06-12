---
title: "Terminal Server Client Error"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by ettienne on 2007-06-26
Whenever I close Terminal Server Client after connecting to either VNC or RDP I get a terminal server client error, reconnect after 30 seconds.
Why is this?

Running on Ubuntu 7.04 FF, connecting to either Ubuntu or Windows computers.

---

### Post by ettienne on 2007-06-27
:confused:

---

### Post by ettienne on 2007-06-28
I keep getting this error.
What's up?
Anyone?

---

### Post by ettienne on 2007-06-28
This is starting to really annoy me, see attached screenshot.

---

### Post by ettienne on 2007-06-28
Screenshot of VNC error.

---

### Post by Cirrocco on 2007-06-28
yeah I get that too.

I see it whenever I tell the client to shutdown or log off.
I don't see it when I just close the RDP window.

pretty sure it just has to do with an unexpected termination of the session.  the software thinks the session ended abruptly when it was the client that terminated the connection.

If I knew how to write any kind of software i'd look into it myself...

---

### Post by nyvalbanat on 2007-06-28
You mean the windows TS, right (aka remote desktop)?
I use rdesktop to connect to my windows boxen  (sudo apt-get install rdesktop). Then run rdesktop <hostname>.

The actual command I run is (substitute $MACHINE for your remote machine):

rdesktop -T $MACHINE -g1280x1024 -r clipboard:CLIPBOARD -r sound:off $MACHINE

---

### Post by ettienne on 2007-06-28
I'm talking about Applications, Internet, Terminal Server Client.

I get the errors when I logout of remote session with a Windows server, or when I close a VNC session - there is no logout for VNC sessions.

I am in and out of various client's Windows Terminal Servers all day, so it is rather annoying to get an error message each time I log out a remote session.

I also VNC to my own servers, a Win2000 server, a Win2003 server and a Ubuntu desktop running VirtualBox with various Windows guests.

So tsclient plays a big role in my working day.

---

### Post by lazyart on 2007-06-30
It's normal.  Annoying but normal.

---

### Post by ettienne on 2007-07-03
Problem solved - I installed WinXP and no more error with TSC.
I prefer more normal than normal.

---

### Post by Mad_Max_1412 on 2008-02-23
Guys,

I get the same error when I close a Terminal Server Client after being connected to one of my WinXP machines.

Is there anyway to close a TSC session without getting this message?

Regards

Max

---

### Post by teeple on 2008-05-28
Not sure if this helps any...

I had the same error when disconnecting from my Servers - very annoying.

I then clicked the DETAILS on the 'reconnect' screen and found that there were two errors that the TSCLIENT application was interpretting as being the issue for my 'abnormal' disconnect.

My keyboard was not set to EN-US and my color depth was set to automatic (defaulted to 24 bit) and it (TSCLIENT) wants 16 bit colors.

So - I changed those two items and now when I disconnect - I don't get the annoying 'reconnecting' error.

Try that.
Bill

---

### Post by Mad_Max_1412 on 2008-05-29
Hi,

When I open TSC, I went to the Display tab and have tried setting the colours to 256, 16-bit and 24-bit.  This didn't resolve the issue.

On the Local Resources tab, I changed the Keyboard from "blank" to en-us, along with the 3 combinations of colors above, but no luck.

It's very annoying when you are finished remotely connecting to a computer to close the TSC program only for it to say that an error has occurred and you then have to click "Cancel" (which takes you back to the main TSC window) and then the close button.

Was this where you wanted me to look as far as colors and keyboard?

Regards

---

### Post by pebs on 2008-06-02
I fixed this problem by changing the protocol from RDP to RDPv5. Hope it helps.

---

### Post by Mad_Max_1412 on 2008-06-02
The only protocol that works for me is VNC, probably because I have VNC client on the remote XP computer.

I tried RDP and RDPv5 but they both came back immediately with an error.

---

