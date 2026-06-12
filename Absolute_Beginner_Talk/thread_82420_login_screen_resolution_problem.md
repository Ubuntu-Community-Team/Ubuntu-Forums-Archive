---
title: "login screen resolution problem"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by LamB on 2005-10-26
when i start a session my screen res. is correct(1280x960), but the problem is at the login screen: it´s set at 1600x1200, how do I change it to 1280x960?     thanks

---

### Post by LamB on 2005-10-26
???

---

### Post by stuporglue on 2005-10-26
> 
when i start a session my screen res. is correct(1280x960), but the problem is at the login screen: it&#180;s set at 1600x1200, how do I change it to 1280x960? thanks

Are you comfortable editing config files and possibly breaking something? If so, you could try this. 

Make a backup of /etc/X11/xorg.conf
Edit xorg.conf. You should find a section "Screen" with several iterations similar to this:
```

	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480" 
```

The list of resolutions is two things. First, it's a list of allowed resolutions, second, it's an order of priority. Try swapping the first and second ones so that 1600x1200 is second (if you want it available sometimes), or just delete the 1600x1200 option if you really don't want to ever get it. 

I think this should fix your GDM. There's probably a better way, but that's all I can think of.

PS. It looks like you only waited 10 minutes for a reply. This is a forum, not live chat. If people know the answer, they'll answer. If not, bumping your thread has the potential to annoy people.

---

### Post by LamB on 2005-10-26
ill give it a try, thanks

---

