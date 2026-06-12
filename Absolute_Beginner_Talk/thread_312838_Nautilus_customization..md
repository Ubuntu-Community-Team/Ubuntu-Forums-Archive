---
title: "Nautilus customization."
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2006-12-05
I know you can change background colours and images in Nautilus, but is there a way to do it in the side panel in Nautilus windows?

(see screenshot)

Thanks.

---

### Post by ciscosurfer on 2006-12-05
I don't know if these help, I did a quick search on Google:[LIST=1]
[*][http://www.linuxselfhelp.com/gnome/users-guide/custom.html](http://www.linuxselfhelp.com/gnome/users-guide/custom.html)
[*][http://www.gnome.org/learn/users-guide/2.0/ch07s08.html](http://www.gnome.org/learn/users-guide/2.0/ch07s08.html)
[*][http://docs.sun.com/app/docs/doc/817-3848/6mjdpedit?a=view](http://docs.sun.com/app/docs/doc/817-3848/6mjdpedit?a=view)[/LIST]

---

### Post by sunexplodes on 2006-12-05
I completely appreciate the effort, and there was some cool info in those pages that i wasn't aware of, but nothing that completely solves my questions. 

That side panel i'm talking about has a few different views, and SOME of them allow for backgrounds to be customized, but not the view I prefer using, unfortunately, which is the "Places" view. 

Does anybody know of a file I can edit or a command I can use to enable more options, or anything like that?

---

### Post by dunomous on 2007-01-25
I agree, I'd also like to place an image there. I've seen somewhere on this forum where you actually change the values of the colors. 

Also, is there anyway you can have the background image stretch instead of repeat? I'd really like it to be fixed.

---

### Post by ardchoille42 on 2007-01-25
Open the configuration editor: gconf-editor 
Go to apps/nautilus/preferences and look at the side_pane_background_filename key.. it sounds like you can add a picture filename there and just restart nautilus to have an image in the side panel. I haven't tried it, but it sounds like what you are wanting.

---

### Post by dunomous on 2007-01-25
I'm not quite sure why that didn't work. I restarted both nautilus, login, and my computer. I tried to just simply change the background color of the panel and that did not work. I tried multiple combinations:

 **1)** side_pane_background_color set to #000000 with side_pane_background_filename set to null and side_pane_background_set left unchecked.

 **2)** side_pane_background_color set to null, a correct file path to an image set for side_pane_background_filename, and side_pane_background_set both checked and unchecked.

 The first, I tried both restarting nautilus and my computer. The second, nautilus and my session. None of this has worked. I'm perplexed as to why.

---

### Post by ardchoille42 on 2007-01-25
That's quite odd.. I was sure that would work.

---

