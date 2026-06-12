---
title: "Reinstall broke my website T-T"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by eDRoaCH on 2008-03-29
So I have my laptop set up as a triple boot system (Vista/OSX/Ubuntu 7.10) and am loving it. I have been using ubuntu to get back into web coding as being able to live-edit the server and therefore seeing changes I make to PHP is just wonderful. 

Amazingly, out of the 3 OSes, Ubuntu was the one that died today. no problem, boot to the live cd, make a backup of home and /var/www and reinstall. 

The way I had things set up for dev before was I made a group called 'web' and added root and my user to it. So I did the same thing again, and copied the files over (thankfully I hadn't started the mysql side yet!) and changed the permissions as they were before (owner root, group www) 

Bluefish opens everything beautifully for editing. however [http://localhost](http://localhost) gives

```

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

```

I tried checking permissions and re-saving all the files in Bluefish, (I just couldn't get the hang of Scream) and still no luck.

I stayed up late tonight to get this system back up, I was hoping to spend the day tomorrow delving into the MYSQL side of things since it is Saturday. I would really appreciate some help, I want to get back to coding!

(as an aside, wow. I am a VERY experienced windows user (since dos/3.11) and I have NEVER gotten my system tweaked just the way I like it so fast as I just did with Ubuntu)

Oh- one other minor detail. I cant seem to find the 'cool' (easier to use) wireless config tool I used to have in my system tray. I have the one that I have to type in the SSID. Where's the one that lists em for you?

---

### Post by igknighted on 2008-03-29
I thought all website data in Ubuntu's version of httpd was to be owned by the user www-data?

As for the wireless applet, NetworkManager is probably what you want.  Should be installed and activated by default, just left click it to display available networks (in gnome), or right click it and select them (in KDE).

---

### Post by eDRoaCH on 2008-03-30
well after being up till 1:30 last night, i rebooted and it was dead again. Not sure what is going on, My idea is it has something to do with my recently installing wine and ies4linux in possible combination of the fact I run compiz on an intel 965. It worked fine for weeks till i got wine and ies4linux installed.

anyway, back to the same place (other than compiz and wine/ies4linux) where I cant access local host with the exact same error as the first post. The files get copied off a fat2 drive so there shouldn't be any security data on them. Tried  a chown -R of the var/www directory to my user with no luck, also changed the group to www-data through nautilus with no luck.

what is the proper way to do this? who is the default owner and group for /var/www and what does apache use? how do i add myself to the right group so I can edit the server live, and how should i set the permissions?

I appreciate any help...

---

