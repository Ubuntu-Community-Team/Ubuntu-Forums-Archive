---
title: "Auto-darken on demand for light sensitivity/photophobia?"
date: 2007-05-25
forum: Assistive Technology &amp; Accessibility
---

### Post by Wartooth on 2007-05-25
I was wondering if there was anything out there, or any way possible to somehow get the screen to darken on demand in the same way that it does when it is asking for a password in order to continue.  

Light colored applications and web pages are absolute torture, causing headaches and eye strain.  Turning my monitor settings down do not do enough, but I have noticed a wonderful relief when getting into Synaptic or something else requiring my password.  Lenses would not provide a very good solution as I'd have them on and off constantly, my website and many that I frequent have dark themes, and my desktop is a very dark theme as well. 

Can that somehow be manipulated in order to alleviate this problem and assist those with light sensitivity? (I'm squinting as I type this...)

Thanks.

---

### Post by cerdiogenes on 2007-05-26
Hi Wartooth,

I opened this bug ref against the gnome-mag component: [http://bugzilla.gnome.org/show_bug.cgi?id=441491](http://bugzilla.gnome.org/show_bug.cgi?id=441491)

If you are registered to the bugzilla tool you can add your mail to the "Add CC:" field an click the button "Save Changes". This way you will be notified when I start to work on it.

I don't know when I will be able to work on it due the lack of time, but I will always remember about it when visiting the gnome-mag bugs page.

Best regards,
Carlos.

---

### Post by ubz on 2007-05-27
> **Wartooth said:**
> I was wondering if there was anything out there, or any way possible to somehow get the screen to darken on demand in the same way that it does when it is asking for a password in order to continue.  


Hi, I have severe light sensitivity so I can relate.

For the ubuntu desktop background I use no wallpaper with black background.
I sometimes use the high contrast black inverse themes...but find the bright white highlight color...way to bright.  It's the only problem I have with those themes.
I use Firefox browser which allows background color, text and link colors to be customized. The options to not allow websites to use their own colors and fonts must be set. (Edit-Preferences-Content Tab)

---

### Post by Wartooth on 2007-05-28
Carlos, thank you very much for submitting that and considering work on it.  That is very kind of you and deeply appreciated :)

ubz:  I, too, have 'black' wallpaper.  I've had problems with some of the things that some dark themes do to webpages, fields and such.  I've found one theme that doesn't have tooooo many conflicts (like white text on a yellow field...white on white...all sorts of crazy things I've tried) and it has been a huge help.  It changes things like OO.o writer and text editors to a grey background with white text.  Sooooo much easier to live with.

I've also tried messing with the stuff that forces changes on websites, but didn't seem to like it much.  I think I might try it again soon, though.  I do appreciate the suggestions!  

Does this board have other template options like some vBulletin boards I've seen?  I tried looking for it, but didn't seem to find it in the user area.  This one is a bit bright for me, too, I'm afraid.  It's easier to visit during the day than at night, though. 

Thanks again for the replies :)

---

### Post by ZenOswyn on 2007-06-02
I've got a little bookmarklet I hacked together (originally called Zap Colors), this one makes web page white text on a black background. It doesn't look very pretty, but it gets the job done. 

Here's the code. 
```

javascript:(function(){var newSS, styles='* { background: black ! important; color: white !important } :link, :link * { color: #0000EE !important } :visited, :visited * { color: #551A8B !important }'; if(document.createStyleSheet) { document.createStyleSheet(%22javascript:'%22+styles+%22'%22); } else { newSS=document.createElement('link'); newSS.rel='stylesheet'; newSS.href='data:text/css,'+escape(styles); document.getElementsByTagName(%22head%22)[0].appendChild(newSS); } })();

```

Create a new bookmark on your bookmark tool bar and paste that code into the location, should work fine.

---

### Post by ubz on 2007-06-03
> **ZenOswyn said:**
> 
Create a new bookmark on your bookmark tool bar and paste that code into the location, should work fine.

Hi, I created a bookmark on the Firefox bookmark toolbar.  And created an htm file for the bookmark  to point to.  Do I paste the code into the htm file and if so does it go between the head tags or am I missing something.  Thanks.

---

### Post by ZenOswyn on 2007-06-04
No, you just copy and paste that into the "Location" box when adding the bookmark.

---

