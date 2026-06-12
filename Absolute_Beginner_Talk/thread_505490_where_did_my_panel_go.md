---
title: "where did my panel go?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by lunamystry on 2007-07-20
So i decide to try KDE and see which is better, I LOVE it I dont know which is better between it and gnome. I was struggling to enable desktop efeects though so i press alt+F2 and run compiz --replace. it works fine. I play around with the cube hoping to finally get it to do what i saw on this one video on youtube, anyway i notice this little green ball that i was going to ask about later if I couldnt figure it out I decide to take a screenshot and maybe include it. I open opera to post a question about the little green ball (its for updates i thinnk). I tried to open this green ball by moving the mouse cusor to the corner then clicking it. after doing that I noticed that opera was not shoowing anynore, I moved around with alt+tab and found it but it was maximised and not all showing, only a corner was showing and when i opened other windows tgey didnt have borders. I ran compiz --replace again and it was fine but my main panel was gone. i still don have it. How can i bring it back?

thank you for reading such a long and non techinical paragraph.

---

### Post by BlahMan_of.Doom on 2007-07-20
I'm not quite understanding everything, but do you have emerald installed? If you're not sure, type
```
sudo apt-get install emerald
```

Then, type ```
compiz --replace && emerald
```

---

### Post by davidjmayo on 2007-07-20
> little green ball (its for updates i thinnk). 

Yes it is for updates. It is Adept the kubuntu package (and update) manager. [If you read other posts and see people talking about Synaptic that's just the Gnome equivalent.] It's just looking for new updates (security patches etc) and is usually visible for only a few secs. If you right click on it you will see it says "adept update notifier"

just let it do it's stuff. If there are are updates you see a red triangle with "I" in it. Click that to get the update(s)

---

### Post by lunamystry on 2007-07-20
> **BlahMan_of.Doom said:**
> I'm not quite understanding everything, but do you have emerald installed? If you're not sure, type
```
sudo apt-get install emerald
```

Then, type ```
compiz --replace && emerald
```

I just installed emerald and my borders have vanished :mrgreen: I think this is because i also have GL desktop installed. Oh I also downloaded the kubuntu desktop to install maybe thats also why the two (gnome and KDE) may be clashing.

Oh dont i need beryl to run emarald? 

My apologies for the any ambiguity i wanna say a lot in few word. :rolleyes:
Oh about the desktop, I logged out and back in again and my desktop was back

I think I got it right. I diabled desktop effects using GL desktop, chose a theme using emerald then enabled desktop effects again. 

Thank you for your time

---

