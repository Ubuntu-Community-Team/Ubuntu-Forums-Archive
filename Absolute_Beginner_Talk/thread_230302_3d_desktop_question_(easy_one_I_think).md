---
title: "3d desktop question (easy one I think)"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-05
Hi all,

I've got the marvellous 3d desktop installed, and everything is working fine. However, I have 3 grey screens when I go into it. By typing...

```
3ddesk --aquire=100
```

... into the terminal solves the problem. However, when I reboot, the screens are all grey again.

Is there a line of code that I can add to the 3ddesktop.conf file that will sort this out??

Thanks in advance.

---

### Post by ylixir on 2006-08-05
i'm not really sure how you have your system setup, but assuming you are running gnome, the easiest way to run that command when you log in is to add it to the "startup programs" tab in the dialog box that comes up when you click "System->Preferences->Sessions"

---

### Post by cheway on 2006-08-05
Hi, I appreciate the reply.

I should have been more specific before, my apologies. Yes, I am running GNOME, and I also should have said that I already tried entering "3ddesk --aquire=100" into the sessions menu. I'm not sure if there's something else I need to do or activate though.

Any ideas anyone?

---

### Post by ylixir on 2006-08-05
where do you start 3ddesk to begin with?  have you tried adding the --aquire there?

---

### Post by kerry_s on 2006-08-05
I have the> 3ddesk --acquire < in my startup programs and it works fine. Then the other commands i use are in my launcher. Pics->
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=13883&stc=1&d=1154824434[/IMG]
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=13884&stc=1&d=1154824434[/IMG]

---

### Post by cheway on 2006-08-05
LMAO, how embarrassing - if you take a look at my first post, you'll see that I have been mis-spelling "acquire" - it has a 'c' in it!!!

Thank you both of you, it's working now. Now I just need to work out how to make the Wallpapoz daemon run on startup....

Kerry, are you using different wallpapers on each workspace? If so, are you using Wallpapoz in GNOME?

My face is still red.....

---

### Post by kerry_s on 2006-08-05
Hey cheway, I only use one wall paper and yes it is gnome. I also run duel monitors. Here's my pics->
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=13886&stc=1&d=1154827278[/IMG]

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=13887&stc=1&d=1154827278[/IMG]

---

### Post by cheway on 2006-08-05
Thanks for getting back to me kerry.

I'm going to have to pick your brains over something else now if that's ok :) 

How are you running dual monitors? I'm using a laptop, but what I want to do is use a television as a secondary monitor for watching movies. However, I would like to be able to still use the laptop for work, chatting etc whilst the movie is playing. Is this possible?

ANOTHER thing I've just noticed - I love the CPU, RAM etc information you have on your desktop - is this embedded? How did you get this??

Sorry for bombarding you with questions here, but I've trying to do these two things for ages!

---

### Post by kerry_s on 2006-08-05
"How are you running dual monitors?"
I use nvida card with duel head support and two monitors. I'm not sure what your running on your laptop so i don't know if you can do that, i've never tried computer+tv yet.

"I love the CPU, RAM etc information"
That app is conky system monitor, do a search for conky on the forum there's a long thread(how-to) on how to get a beautiful conky.

---

