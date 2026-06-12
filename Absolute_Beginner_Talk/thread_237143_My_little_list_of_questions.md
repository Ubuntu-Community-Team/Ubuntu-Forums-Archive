---
title: "My little list of questions"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by _hyphen on 2006-08-15
I have been playing with ubuntu -dapper- (rather happily) for a while now. It has replaced xp as my OS on my secondary pc. While I have been reasonably comfortable with doing things on it, there are a couple specific issues that I have yet been able to address as fully as I would like.

If anyone can help on any individual or all of these items, I would greatly appreciate it! I am not afraid of the terminal at this point and am comfortable with pretty much any depth of instruction required to make them happen.

That being said, here are the specific things I have been after

1- Replacing the ubuntu main menu icon with a different icon altogether. Can this be done? I don't mean it has to say "start" on the button, I would just kinda like something more rectangular in shape as my button, even if it just said something like "menu". Its aesthetic. I just want the button itself changed, I have the desktop otherwise tweaked to how I like it.

2-Is there a setting that will allow application windows, when maximized, to in fact Cover the main taskbar? This PC has a very small monitor so I need to make the most of my screen real estate (plus if I am in an app, I just frankly prefer that app to be the entirety of what I am viewing)

3-This one is kind of weird I imagine - can anyone point me to something, if it exists, that would instruct me on how to embed a terminal window into the desktop so to speak? That is to say, it wouldnt be over other windows, but when the desktop were visible it would be possible to just click in the terminal window and go to work? does that make sense? I know what I mean, I just don't know if I am explaining it very well =/ sorry. embedded is really the best I can describe it, literally just always there and kinda melded into whatever the background is through the transparency setting.

4-I have done fine with finding and installing various codecs for multimedia players and their associated firefox plugins, but one thing that has been tripping me up, is that while many of them let you define certain playback options, I haven't been able to find any setting that allows the browser plugins playback to loop . I know there is , for example, in mplayer a way to define infinite loop through the config file for the program itself if outside of the browser, but the same setting did not work for the embedded media plugin. Any advice on this one? Can playback within the browser window be looped for video? While I am partial to VLC, I would use whichever player would allow this one little tweak because its just eating at me that I haven't been able to figure it out.

Anyhow, I know these are all kind of silly in the scheme of 'importance', but it would really help with the personalized feel, I have always been picky about my PCs being how I want them, not how the OS gave itself to me. Plus knowledge is a good thing :)So thank you in advance if there are answers to any or all of these somewhere out there. feel free to not go into detail if there is an existing guide, a link is more than fine.

ps-I can't seem to run xgl/compiz on this pc,(vidcard probably to lowly, older geforce2) so if any of the solutions involve those, then I am s.o.l.

thanks!

Dw

**edit to specify version**

---

### Post by ComplexNumber on 2006-08-15
1) yes, but the "Start" button icon is dependent upon the icon theme. its just a case of changing the gnome-main-menu.XXX icon within the theme. the themes are located either in /home/<username>.icons or /usr/share/icons.

2) right click on the panel and select auto hide.
however, you will notice that 6 pixels are still showing. if you want to hide these, let me know and i'll show you how (ie changing some values in gconf-editor).

3) not that i'm aware of if i understand you. why not just add the terminal to your panel?

4) i can't help you there because its not functionality that i've ever sought.

---

### Post by David Corrales on 2006-08-15
For the terminal thingie, you might wanna check this program
[http://tilda.sourceforge.net/wiki/index.php/Main_Page](http://tilda.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by _hyphen on 2006-08-15
A-bi
thank you, your answer to question One was exactly what I was needing there, I appreciate the information

in regards to question two, I was just looking for application windows to be able to open over top of the bar rather than using autohide. essentially wanting to undo its default "stay on top" state that it seems to have. again, this is just a personal quirk of mine, never been a fan of hiding bars

David-
thank you for the link. It seems to be having some issues at the moment with opening,so I am not yet sure where or what it is pointing to, but I will give it a shot when I get home in about an hour. :) 

Any further advice on these subjects is warmly welcomed :-D 

d

---

### Post by ComplexNumber on 2006-08-15
i found a solution for you for your 2nd question, but it means deleting the standard panel and installing a new one. it has the functionality that you need. click [here]("http://gnomefiles.org/app.php/Foopanel"). you can see a screenshot [here]("http://foopanel.berlios.de/foopanel/_detail/screenshots/prefs-dialog.jpg?id=screenshots&cache=cache") that shows the functionality that you want.
thats the beauty of gnome - if the standard applications aren't quite right, there is always something that has the exact necessary functionality.

---

