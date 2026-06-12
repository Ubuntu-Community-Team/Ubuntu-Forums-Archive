---
title: "Windows Network shares"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by d2843 on 2007-05-14
I am having trouble accessing Windows shares over the network in Nautilus (although it works fine in Konqueror). I can browse the network to some extent, but when it gets to the shared folders I get this...

> The filename "ASIANDVINYL" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

I would like to be able to use gnome without having to open the KDE file browser for network access. Please help!

---

### Post by dannyboy79 on 2007-05-14
nautilus is nortoriously horrible at handling browsing to shares. however, if you chose the option from the Places pull down menu, and chose Windows SMB Share, enter the server name, and click connect, it'll put a icon on your dekstop, then if you double click it, it should pop up a password and username box, enter them, and you'll see your windows share. for some reason, if you go thru, network, then chose windows, then chose your box, you get these weird errors, it was a problem in dapper as well. also, it amybe sounds as if your mime-type for that extension may be corrupted or wrong, what exact file type are you trying to open over the network?

---

### Post by d2843 on 2007-05-14
hey it worked! thanks a lot!

---

### Post by dannyboy79 on 2007-05-14
i do have to comment on this! i actually hadn't tested it in fiesty and it actually works on my ubuntu when I go to places, then network, then windows network, then I chose my winxp pro machine and it asks me to enter my keyring password and then I see all my winxp pro shares. So I am glad to see that they have fixed somethign that didn't work!!!

So I wnder why your isn't working? can you ping by hostname? if not try adding the ip address of your winxp machine to your hosts file which is located in your /etc/ folder. OR just open the networking gui under system, admin, and add it there. I have all my machines set to static ip so it's easy to add a hostname and it's ip but I am not sure what you'd do if you use dhcp. if you don;t care I can understand, I am merely trying to find out why your box isn't working like it should. did you install samba?

---

### Post by d2843 on 2007-05-15
I'm doing all this on the network at work, so I can't really adjust settings on everyone else's xp computers. I believe Samba is installed. I just think its weird that i can access it fine in Konqueror but not in Nautilus.

As a n00b, I request an explanation from all you 1337 people out there. Thanks for your help so far!

---

### Post by dannyboy79 on 2007-05-15
well Like I said I am sure why that is but I don't have any problems in my little network. I have a winxp pro machine, a ubuntu fiesty machine, a xubuntu fiesty laptop, and 2 xbox's with Xbox Media Center that's able to access smb shares on all machines in my network. does you work network have a WINS server? if it does you should install winbind and change your /etc/nsswitch.conf file so your machine gets registered with the WINS server. here's a good guide for that. and again, I can't tell you why Konq works and Nautilus doesn't without possible doing some more stuff on your box like installing winbind.
[http://ubuntuforums.org/showthread.php?t=88206&highlight=hostname+resolution](http://ubuntuforums.org/showthread.php?t=88206&highlight=hostname+resolution)

---

