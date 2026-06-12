---
title: "Xubuntu and samba... Possible?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-08-30
Hello.
I'm installing Xubuntu and I need to work on a windows network sared folder.
I know that Tunar doesn't support samba browsing. 
What other option do I have? 
I tried to install nautilus but network browsing seems not working when typing smb:// or simply the full addres that works in ubuntu.

Is absolutely not possible to browser windows network files in Xubuntu?

Thank you

---

### Post by Kosimo on 2007-08-30
Any idea guys?

Plz!

---

### Post by sawjew on 2007-08-30
Sorry I didn't get back to you a bit sooner but I had just got home from work and had to go and have tea.  Anyway hopefully I can help you.  You can use an application called 'pyneighborhood'.  It is in the repositories you can install it by opening a terminal and entering ```
sudo apt-get install pyneighborhood
```

There is a guide to use it here [http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html]("http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html") but you don't need to compile it from source if you are using Feisty.  I am not sure if it is in the repositories for earlier releases.

If it doesn't work using these instructions you can try running it as root using ```
gksu pyNeighborhood
```

If you change the mount directory in the preferences to ```
/media/
```

then when you mount a network share it should show up on the desktop as a mounted drive.  I think you will have to run it as root to do this though.

Anyway pyNeighborhood works really well and is very easy and will even work when networking to Windows Vista where Nautilus will not.

I hope this helps you out.

---

### Post by Kosimo on 2007-08-30
> **sawjew said:**
> Sorry I didn't get back to you a bit sooner but I had just got home from work and had to go and have tea.  Anyway hopefully I can help you.  You can use an application called 'pyneighborhood'.  It is in the repositories you can install it by opening a terminal and entering ```
sudo apt-get install pyneighborhood
```

There is a guide to use it here [http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html]("http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html") but you don't need to compile it from source if you are using Feisty.  I am not sure if it is in the repositories for earlier releases.

If it doesn't work using these instructions you can try running it as root using ```
gksu pyNeighborhood
```

If you change the mount directory in the preferences to ```
/media/
```

then when you mount a network share it should show up on the desktop as a mounted drive.  I think you will have to run it as root to do this though.

Anyway pyNeighborhood works really well and is very easy and will even work when networking to Windows Vista where Nautilus will not.

I hope this helps you out.



Hey Mate!!

This is exactly the answer I was waiting for. Even if I understood that is pyNeighborhood what I have to use.  I didn't realize I shoud open it in gksu mode. 
Anyway now I'm having some problemsm but I'll try to solve by myself on the tutorial you just sent.  this is the error I get: (failed to scan workgrup)

So, now I have the tool I need to play with.

Thank you so much and enjoy your tea in the magic Australia, (I've been living there last year  by the way :) )

---

### Post by Kosimo on 2007-08-30
Finally I did it :)
I couldn't scan the workgroup and computers by browsing, but if inserting manually it works perfectly.  :)

Thank you so much!

---

### Post by Kosimo on 2007-08-30
Oooops!!

More questions are comming!! :)

Now that is done, 
can I do some way to mount it automatically each time I turn on the computer?

---

### Post by Kosimo on 2007-08-30
Is absolutely necessary to run pyNeighborhood in sudo mode in order to make it work?

---

### Post by 00l0 on 2008-05-20
> **Kosimo said:**
> Is absolutely necessary to run pyNeighborhood in sudo mode in order to make it work?

i'm also interested in pyNeighbourhood usage instructions, if you managed to get it working and could let me know that would be great!

merci

ps. m'ho pots enviar per privat si et sembla millor : D

---

### Post by sawjew on 2008-05-20
You do not need to run pyNeighborhood in sudo mode.  I have been using it with gksu for quite a while and have only just discovered how to use it without thanks to this [site]("http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html").

All you need to do is open a terminal, enter 
```
sudo chmod +s /usr/bin/smbmount
sudo chmod +s /usr/bin/smbumount
```

This allows users to mount samba shares.

Them make sure you mount to a directory in your Home so that you have full read/write access and you're done.

I have just get this working successfully on Xubuntu 8.04 with no issues at all.

---

