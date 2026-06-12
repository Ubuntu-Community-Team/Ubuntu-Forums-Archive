---
title: "Succinctness"
date: 2011-03-24
forum: Art &amp; Design
---

### Post by Personal Jesus on 2011-03-24
I love computers. Truly, I do. I also love principles.

Linux is based around the principle of complete and total freedom. I can't help but love that. But, I'm torn, you see? OS X has completely shocked me. Since I first got my Macbook Pro, I couldn't believe how user-friendly it was. It's changed how I view life and how I use my computer. However, I feel there's a certain. . . emptiness. I miss my days of Ubuntu, even though they weren't as perfect and well-polished as OS X. Today I had a marvelous idea.

How about taking Ubuntu and turning it into an even simpler interface than OS X? The simplicity in OS X is what makes it breathtaking, not to mention the grand artistic overtones. Surely it is possible to combine these two great principles, freedom and simplicity, is it not?

The reason I am making this thread is that I'd like to ask for help. I am in no means as educated as some of you may be in regards to Ubuntu (though I am not an idiot). Tell me any possible ways that I could implement the user-friendliness and simplicity of OS X into Ubuntu. Since I have just started this, the first thing that came to mind was Gnome-Do. I've also considered completely removing all the panels and figuring out a way to access everything in a simpler and more convenient way. (Not sure how yet, but I imagine I could find a program similar to Gnome-Do that would implement this.)

---

### Post by Copper Bezel on 2011-03-24
If it's just about task managers and the like, have you played with Unity at all? It's very user-friendly, like something between OSX and Android in terms of getting around.

There are other ways to get a quick, friendly interface, though. I'm a big fan of simplicity, and I use Avant Window Navigator with DockBarX, along with some other little simpler choices like Thunar over Nautilus as the default browser. 

[[img]http://dl.dropbox.com/u/17749392/Screenshots/maxed.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/maxedfull.png)

The taskbar is still there, but I'm a big fan of the Transparency mode used above, which really keeps it out of the way but still easy to access.

[[img]http://dl.dropbox.com/u/17749392/Screenshots/nomax.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/nomaxfull.png)

Compiz's Trailfocus plugin is being used to slightly dim unfocused windows.

A readable theme is a big part of it, too. I'm using Orta and the Faenza icons, which are both a little trendy right now, but for good reason - they're as readable and consistent as Aqua.

I can see the attraction of Gnome-Do, but it wouldn't help for task switching. If you removed the task bar, you could still use Compiz Scale or Alt+Tab to switch windows, but Scale wouldn't help for minimized windows (it can be tweaked, but the results are imperfect) and Alt+Tab is sloppy with more than, say, five windows open.

---

### Post by Personal Jesus on 2011-03-24
> **Copper Bezel said:**
> If it's just about task managers and the like, have you played with Unity at all? It's very user-friendly, like something between OSX and Android in terms of getting around.

There are other ways to get a quick, friendly interface, though. I'm a big fan of simplicity, and I use Avant Window Navigator with DockBarX, along with some other little simpler choices like Thunar over Nautilus as the default browser. 

[[IMG]http://dl.dropbox.com/u/17749392/Screenshots/maxed.png[/IMG]]("http://dl.dropbox.com/u/17749392/Screenshots/maxedfull.png")

The taskbar is still there, but I'm a big fan of the Transparency mode used above, which really keeps it out of the way but still easy to access.

[[IMG]http://dl.dropbox.com/u/17749392/Screenshots/nomax.png[/IMG]]("http://dl.dropbox.com/u/17749392/Screenshots/nomaxfull.png")

Compiz's Trailfocus plugin is being used to slightly dim unfocused windows.

A readable theme is a big part of it, too. I'm using Orta and the Faenza icons, which are both a little trendy right now, but for good reason - they're as readable and consistent as Aqua.

I can see the attraction of Gnome-Do, but it wouldn't help for task switching. If you removed the task bar, you could still use Compiz Scale or Alt+Tab to switch windows, but Scale wouldn't help for minimized windows (it can be tweaked, but the results are imperfect) and Alt+Tab is sloppy with more than, say, five windows open.

Thank you for the reply.

I really like your ideas there. I was considering Thunar. What I think would be best is figuring out how to implement a task-switcher that's similar to Expose on OS X. See, I find that's the most user-friendly way of accessing my applications. Is there a possible compiz mod/tweak that allows that? The point of Gnome-Do, by the way, was for just application launching or file system browsing. The idea is that I want to make the taskbar (aka panels) as useless as possible and as neglected as possible. That wasn't the greatest way to put it, but like. . . I mean that I want them to only be needed in dire situations. I don't like how they set up panels and I honestly don't see why there can't be a simpler way of accessing all the apps and programs. Hence, Gnome-Do. The main goal is that I want there to be absolutely no need for a panel at all. (That's not precisely the main main goal, but it's part of the big picture.) Make sense?

edit: Let me elaborate some.

In my OS X experience, I have become so used to functioning almost entirely from the keyboard or the mouse that I do not even use my dock for anything but program quitting. (You know, the ones that you can't get to via Expose.) It'd also help if there were some way to find a workaround in Ubuntu so that all your applications can easily be terminated at any time (Does Gnome-Do have a feature like that?). That way, I don't need any user interfaces such as the panel or a dock.

Also, as for notifications: Growl seems promising in that respect.

---

### Post by Copper Bezel on 2011-03-24
In Compiz it's called Scale, and it's my primary method of task switching, too:

[img]http://dl.dropbox.com/u/17749392/Screenshots/expose.png[/img]

The problem is that it doesn't show minimized windows, because mapping them takes too long (normally, the pan effect is instantaneous.) However, you can use [this](http://ubuntuforums.org/showthread.php?t=976002) python script to run a tweaked version of it that *will* raise minimized windows, with a slight delay. I have my upper screen corners set to Scale and the python script set to clicks at the same corners, so that if I flick the corner and find that the window I wanted was minimized, I can click to draw it up into the "expose."

---

### Post by Personal Jesus on 2011-03-24
I've thoroughly got things setup now.

The thing I need help with, though, is modifying Firefox to be more compact and a general gnome gui theme that's compact. Any suggestions?

---

### Post by tgalati4 on 2011-03-24
sudo apt-get install google-chrome

---

### Post by Copper Bezel on 2011-03-25
> The thing I need help with, though, is modifying Firefox to be more compact and a general gnome gui theme that's compact. Any suggestions?

Actually, there are a number of add-ons and tutorials around for reducing Firefox's impact on screen real estate, like [this one]("https://addons.mozilla.org/en-US/firefox/addon/hide-caption-titlebar-plus-sma/") and [this one]("https://addons.mozilla.org/en-us/firefox/addon/hidemenubar/"). You can also get extensions to hide the scrollbars. I use Opera, personally, but with the right tweaks, Firefox can be more compact.

If you're serious about reducing the UI to the bare essentials, you could also consider using Compiz to hide the titlebar for maximized windows, by opening up ccsm and entering 

```
!(state=Maxhorz & state=Maxvert)
```

in the Decoration Windows field of the Window Decoration plugin. You could then go to General Options -> Keybindings and set Toggle Window Maximized to Top Edge+Button One, so that clicking the top edge of the screen would restore the window and bring back the window controls.

Again, I'm compelled to push Orta as a simple GTK theme. Among its many options is one for reducing scrollbar size, which is very nice, and it uses 1px borders and border cropping for maximized windows.

Oh, and share your results! I want to see what you came up with. = )

---

### Post by Personal Jesus on 2011-03-25
So far, so good.

[IMG]http://img851.imageshack.us/img851/5272/screenshotxy.png[/IMG]



All I need to figure out now is skinning Pidgin. :p I remember doing it a while back, but that was forever ago. X_X Nonetheless--what do you think so far?

---

### Post by Copper Bezel on 2011-03-25
Very clean. = ) And I guess you're using Scale for window selection, then? Do you have anything for a system tray, though? I guess if it's a desktop, you wouldn't need a network or battery icon, but some daemons like to run controls there (like Tomboy, Dropbox, etc.)

---

### Post by Personal Jesus on 2011-03-25
> **Copper Bezel said:**
> Very clean. = ) And I guess you're using Scale for window selection, then? Do you have anything for a system tray, though? I guess if it's a desktop, you wouldn't need a network or battery icon, but some daemons like to run controls there (like Tomboy, Dropbox, etc.)

Yup, scale is amazing. It's better than Expose. I don't have any system tray at all. I've been using Gnome-Do for application launching.

---

### Post by Copper Bezel on 2011-03-25
Very cool - I love the result. It's nice to have a clean workspace. = ) (Oh, hey, do you actually want the desktop icons? If you don't, you can deactivate them in the Gnome configuration.)

---

### Post by Personal Jesus on 2011-03-25
> **Copper Bezel said:**
> Very cool - I love the result. It's nice to have a clean workspace. = ) (Oh, hey, do you actually want the desktop icons? If you don't, you can deactivate them in the Gnome configuration.)

Actually, I have the desktop icons as a fail safe. If Gnome-Do unexpectently quits, I use the icon to restart it. If there's a better solution, please inform me. XD

Also, I had a question. How do you get a script to run on start in the startup manager? I've got it added and such, but apparently I don't have something correct in the 'command' field because it's not opening on startup.

---

### Post by Copper Bezel on 2011-03-27
What script are you trying to run? Ordinarily, putting a command in the list in Startup Applications will do it. (But I'm noticing that my Gnome Do, for instance, fails to run at startup even though it's in the list.)

---

### Post by Personal Jesus on 2011-03-27
> **Copper Bezel said:**
> What script are you trying to run? Ordinarily, putting a command in the list in Startup Applications will do it. (But I'm noticing that my Gnome Do, for instance, fails to run at startup even though it's in the list.)

The script is:

```
         xmodmap -e 'clear mod4'
xmodmap -e 'add control = 0xffec'
```

It's for remapping the CMD key in my MBP's keyboard so that it functions more appropriately with Ubuntu. Yes. I know. Running a MBP on Ubuntu is near blasphemy.

---

### Post by Copper Bezel on 2011-03-27
Well, it's only blasphemy to Steve Jobs. = ) I'd use Mac hardware if I could afford it, but I probably wouldn't use their OS.

If you have that script in an executable text document and the command in your startup applications points to that file, it should work, but it might be running before your keyboard layout gets applied the first time. Try adding a sleep command to the start of the script (like " sleep 10 ") to delay it and see what happens.

---

