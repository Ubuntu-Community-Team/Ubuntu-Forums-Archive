---
title: "[SOLVED] Can't access secure websites..."
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by randalotto on 2008-02-03
So my router and modem have never given me any problems. For months I've had a static IP set up and everything was just peachy...

About a week ago, give or take a few days, I started having connection problems. Sometimes, websites just wouldn't come up.

Now, I realize that certain websites - entirely random ones - will just refuse to load. More universally, however, any page that is secure - https - will refuse to load. It eventually just times out and gives me an error page.

I have tried other computers on the same network / through the same router, and they all load just fine.

Like I said, Firefox was working perfectly and then went crazy out of the blue. Any suggestions for fixing this?

Thanks,

Randy

---

### Post by randy78 on 2008-02-03
Hey Randy!
Randy here... ;)

Did you happen to install Firestarter firewall?

If you did, be sure to check that under the policy>Editing>outgoing connections section, that https (port 443) is allowed access, or you could just set it to permissive...

If you don't have Firestarter or any other Firewall installed, let us know and we'll try to help you get it squashed :guitar:

---

### Post by randy78 on 2008-02-03
Also, if your router's security is set to only allow certain ports, this could be tripping you up as well...

This happens to me when I set my router firewall to MEDIUM security...

Check your router config by going to 192.168.1.1 or 192.168.0.1 and let us know!

---

### Post by randalotto on 2008-02-03
Firestarter is not installed,

and there is nothing in the router settings that should be causing problems. Like I said, I can hook up other computers (both wired and wireless) through the router and access the secure websites. 

This problem is ubuntu-related and started without me taking any actions.... (so far as I know)

EDIT: to add another wrinkle to this, I can access secure websites when running XP in VMWare on this Ubuntu machine... might that suggest a Firefox problem? I don't know enough about how VMWare communicates with the computer to know...

---

### Post by randy78 on 2008-02-04
Hmm...

So in Xp, you can access secure websites using Explorer or Firefox or both?

Try installing Opera in Ubuntu:
sudo apt-get install opera 

Then, try accessing a secure site with Opera and let us know if it works.

Take Care

---

### Post by randalotto on 2008-02-04
Well, opera wouldn't download (couldn't find 64-bit build i guess...)

However, I did install epiphany, and it's having the same problem. No https webpages will load.

---

### Post by randy78 on 2008-02-04
Ok...

It sounds like your machine isn't allowing the connection, and that IPTables might have been screwed up somehow...

Let's try to fix it by installing Firestarter

sudo apt-get install firestarter

After it's installed, open a terminal and type: sudo firestarter and a Configuration wizard will pop up

Configure that to your network settings (or leave default)

Then, go to Policy> Editing>Outbound>select restrictive by default and then right click in the Allow Service box and select add rule 

Select Http from the list, for anyone and then click add
Next, do the same thing but this time, select Https from the list

Try that to see if it opens the port for you.

If you have any trouble with Firestarter, let me know

---

### Post by randy78 on 2008-02-04
Also, in Firefox, go to Edit>Preferences>Advanced>Encryption and make sure that both SSL and TLS are checked, as well as Select One Automatically.

---

### Post by randalotto on 2008-02-04
> **randy78 said:**
> Ok...

It sounds like your machine isn't allowing the connection, and that IPTables might have been screwed up somehow...

Let's try to fix it by installing Firestarter

sudo apt-get install firestarter

After it's installed, open a terminal and type: sudo firestarter and a Configuration wizard will pop up

Configure that to your network settings (or leave default)

Then, go to Policy> Editing>Outbound>select restrictive by default and then right click in the Allow Service box and select add rule 

Select Http from the list, for anyone and then click add
Next, do the same thing but this time, select Https from the list

Try that to see if it opens the port for you.

If you have any trouble with Firestarter, let me know


That worked! 

Thank you very much!!

So now can I change it to permissive? Uninstall firestarter? What now?

---

### Post by randy78 on 2008-02-04
You can set it to permissive if you want, yeah ;)

I leave it set on Restrictive and add only the services I need at any given time, that way my box isn't broadcasting available ports and services for the whole world to see.

Firestarter is a front end to the built in IPTables, and is pretty handy to have around.

If you want to uninstall Firestarter, just open up a terminal and type:
sudo apt-get remove firestarter

Glad that worked out for you

Please mark your post as SOLVED by going to Thread Tools and Mark As Solved, so other people will be able to use the info!

Take Care:popcorn:

---

