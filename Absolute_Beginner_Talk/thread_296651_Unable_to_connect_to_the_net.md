---
title: "Unable to connect to the net"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Drudwyn on 2006-11-09
Hey, I'm an absolute newbie to linux, and I'm having some issues with ubuntu 6.06

I've got full connection using ping or firefox, but Gaim, Synaptic etc. seem unable to connect to the net in any way. I've disabled IPv6 in Firefox, which is the only way I managed to connect via it, but I don't know what to do next.

I've not found any of the documents to be helpful at all, and in the words of Leia, you're my only hope.

Thanks guys,

Drud

---

### Post by tzulberti on 2006-11-10
You should try: sudo dhclient...

---

### Post by Bartender on 2006-11-10
Disabling IPV6 in Firefox only disables it in FF.  Take a read thru this [post]("http://www.ubuntuforums.org/showthread.php?t=87798") for directions on disabling it systemwide.  Make those edits just like how he shows, then restart the PC and see what happens.

---

### Post by Drudwyn on 2006-11-13
ok, thanks.... how do I save the file, I've not got write priveleges using the gui?

---

### Post by Bartender on 2006-11-13
I'm not sure I understand your question.  You know what, I apologize, that link I gave you is confusing because the guy is assuming a certain level of proficiency.
Go to "Applications">"Accessories">"Terminal".  Click the terminal icon and drag to your desktop.  Experienced users are rolling their eyes right now but it works for me.
Now you've got no-brainer access to terminal.  Double-click on it.
The cursor is blinking next to the dollar sign.  Type this in or copy/paste if you can

```
sudo gedit /etc/modprobe.d/aliases
```

It'll ask you for password.  Type it in.  Don't worry if nothing seems to happen, Linux doesn't show asterisks or blobs or any sign of the password keystrokes.  Hit Enter key.  Wait a few seconds.  Gedit opens up and you'll see your modprobe.d/aliases file.  Take a close look at posts #1 and #5 of that link I sent you earlier.  It explains what to do and where to do it.  See in post #5 where he put a little note that says "# 1, 2, 3 new lines"?  That's where you type in or paste 
```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
```

You also need to add the "#" sign to the beginning of the 
"alias net-pf-10 ipv6" line so that it looks like this:
"#alias net-pf-10 ipv6".

Save the file by clicking the "Save" floppy icon and reboot the PC.  If you did this right IPV6 is now disabled across the entire system.  See if your other internet functions work now.

Jeez, I hope I got that down all right...

---

### Post by kousikbiswas on 2006-11-13
Hi I have just installed Ubuntu 606. Please guide me to configure my broadband connection. My ISP use PPPoE . Please help .

---

