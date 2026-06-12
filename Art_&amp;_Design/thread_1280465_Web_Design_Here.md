---
title: "Web Design Here?"
date: 2009-10-02
forum: Art &amp; Design
---

### Post by darksideforge on 2009-10-02
Is this the appropriate forum to ask questions regarding website design and html?  If it isn't, would someone direct me in the proper direction please? Thank you in advance.

---

### Post by alex.rayu on 2009-10-02
Yeah people post that here.

---

### Post by darksideforge on 2009-10-02
Is anyone familiar with generating templates using Artisteer and then editing them using Seamonkey Composer, Kompozer, Screem, Dreamweaver, or other?

I've come up with several templates on Artisteer with drop-down menus. Importing them to Ubuntu and using Seamonkey isn't an issue...as long as I stay in the graphical edit mode...which is fine for editing the first-available menu items. However, in order to add more sub-menus, I have to use the "<source>" tab, and every time I do this, I end up losing part of my formatting (ie: the header I created in Artisteer) disappears.

I don't recall adding anything above the menu or submenu items so the only thing I can think of is some sort of <div> error.

And please keep in mind that I am SUCH A TOTAL NEWB to html that it isn't even funny.

One last side-note is that I know the Kompozer that's in the repos has glitches in 9.04 so I've been using the .8alpha from getdeb. I've also found that I like using gedit more than any of the other html-specific text editors out there like screem, Emacs, et al.

---

### Post by zyxyellowxyz on 2009-10-02
> **darksideforge said:**
> Is anyone familiar with generating templates using Artisteer and then editing them using Seamonkey Composer, Kompozer, Screem, Dreamweaver, or other?

I've come up with several templates on Artisteer with drop-down menus. Importing them to Ubuntu and using Seamonkey isn't an issue...as long as I stay in the graphical edit mode...which is fine for editing the first-available menu items. However, in order to add more sub-menus, I have to use the "<source>" tab, and every time I do this, I end up losing part of my formatting (ie: the header I created in Artisteer) disappears.

I don't recall adding anything above the menu or submenu items so the only thing I can think of is some sort of <div> error.

And please keep in mind that I am SUCH A TOTAL NEWB to html that it isn't even funny.

One last side-note is that I know the Kompozer that's in the repos has glitches in 9.04 so I've been using the .8alpha from getdeb. I've also found that I like using gedit more than any of the other html-specific text editors out there like screem, Emacs, et al.

I'm not familiar with making templates with Artisteer, but I do know some about HTML (been teaching myself for 7+ years, and here's my latest work: [http://jonsjava.com/fcl/](http://jonsjava.com/fcl/) - ignore the ugly alert box, that was a last minute addition). if you could attach or send me the page(s) I could look at them to see if you are not closing something out right.

Also, I don't know if this would work for what you are wanting, but you could always try out Aptana and/or Eclipse (Aptana can be a stand alone or plugin for Eclipse).

---

### Post by Merk42 on 2009-10-05
> **darksideforge said:**
> Is anyone familiar with generating templates using Artisteer and then editing them using Seamonkey Composer, Kompozer, Screem, Dreamweaver, or other?

I've come up with several templates on Artisteer with drop-down menus. Importing them to Ubuntu and using Seamonkey isn't an issue...as long as I stay in the graphical edit mode...which is fine for editing the first-available menu items. However, in order to add more sub-menus, I have to use the "<source>" tab, and every time I do this, I end up losing part of my formatting (ie: the header I created in Artisteer) disappears.

I don't recall adding anything above the menu or submenu items so the only thing I can think of is some sort of <div> error.

And please keep in mind that I am SUCH A TOTAL NEWB to html that it isn't even funny.

One last side-note is that I know the Kompozer that's in the repos has glitches in 9.04 so I've been using the .8alpha from getdeb. I've also found that I like using gedit more than any of the other html-specific text editors out there like screem, Emacs, et al.
Have you tested the validity of the page? It would show if there was a <div> error.  Does using gedit to add a submenu make your header disappear?

> **zyxyellowxyz said:**
> I'm not familiar with making templates with Artisteer, but I do know some about HTML (been teaching myself for 7+ years, and here's my latest work: [http://jonsjava.com/fcl/](http://jonsjava.com/fcl/) - ignore the ugly alert box, that was a last minute addition). if you could attach or send me the page(s) I could look at them to see if you are not closing something out right.

Your website has buttons for valid XHTML and CSS, however your site fails at both (and the CSS button doesn't even work)

---

### Post by zyxyellowxyz on 2009-10-05
> **Merk42 said:**
> Your website has buttons for valid XHTML and CSS, however your site fails at both (and the CSS button doesn't even work)

The CSS has been fixed, and way to be super picky that I hadn't put in a custom link to check it (this website was done within 48hours!).

The XHTML was invaild because of the marquee (which has been removed) and  because it doesn't like the java script I have in there. If you bothered to look at the output, you would have known that.

It has been fixed. And is now 100% valid and the CSS button "works" now.

---

### Post by Merk42 on 2009-10-05
> **zyxyellowxyz said:**
> The XHTML was invaild because of the marquee (which has been removed) and  because it doesn't like the java script I have in there. If you bothered to look at the output, you would have known that.

Oh I know why it was invalid, my point is you had buttons promoting that you had vaild code when you, in fact, didn't.

---

### Post by darksideforge on 2009-10-05
> **Merk42 said:**
> Have you tested the validity of the page? It would show if there was a <div> error.  Does using gedit to add a submenu make your header disappear?

It wasn't a gedit problem...it was, in fact, a </div> error. After the Nav menu, I'd apparently mistakenly deleted one </div> without realizing it and that threw it all off.

I fixed the issue by finding a simliar website online (random Google search), saving it as an .html file, and then pulling both files up in gedit and toggling back and forth while quickly scanning for "changes" between the two files.  Something tells me if I knew how to use the diff function, I could have done it much faster, but my way worked as well.

Also, something else that I've learned is that, for Ubuntu, Seamonkey Composer works M-U-C-H better than Kompozer, including any of the newest builds/fixes of Kompozer.  Having said that, it is IMPERATIVE to ensure that your Composer is saving your altered/edited .html files in the UTF-8 format.....any other format will destroy any work you've done when you attempt to re-publish your "new" .html file out of Composer.

---

### Post by alex.rayu on 2009-10-06
While playing with smart programs, would be nice if you learned html and css. That would leave you with freedom of using syntax highlight editors.

---

### Post by darksideforge on 2009-10-06
> **alex.rayu said:**
> While playing with smart programs, would be nice if you learned html and css. That would leave you with freedom of using syntax highlight editors.

That's exactly what I've been doing. At first it was looking at the Seamonkey Composer screen in one window while making a visual change and then looking at the same page in text in gedit in another window next to it on the desktop, clicking "save" and watching the changes to see which areas of text were affected by which visual change.

The problem I ran into with that (learning that way) is that Composer doesn't exactly create great code...crap starts going everywhere and formatting goes out the window after a few changes.

I installed Amaya last night but haven't gotten to play with it at all...right now I'm just concentrating on Aptana Studio, which I really really like. Of course, I used to love Eclipse so it stands to reason that I'd like the stand alone Aptana.  I like that gedit is fast and light, but now that I'm starting to learn the effects/tools in Aptana, I'm pretty excited.  I haven't done anything "custom" yet, but still just learning by manipulating existing free templates from the 'net and changing them around and clicking "save" and then opening them or refreshing them in Firefox or Shiretoko.

---

### Post by darksideforge on 2009-10-06
---a quick note about my last post---

When I said "opening or refreshing them in firefox", I meant opening them as a file from my hdd, not publishing them to the web or anything nefarious like that.  Sorry for not being clear on that to begin with.

---

### Post by argraff on 2009-10-07
I'd also suggest trying Bluefish - I find it's syntax highlighting and shortcut keys really useful! (disclaimer: I'm using the beta version, which is mostly stable at this point.)

---

### Post by darksideforge on 2009-10-08
> **argraff said:**
> I'd also suggest trying Bluefish - I find it's syntax highlighting and shortcut keys really useful! (disclaimer: I'm using the beta version, which is mostly stable at this point.)

I'm doing some design work this morning. I just downloaded it and am going to give it a try. I'll report back with my comparison to Aptana to see if I like it better.

---

