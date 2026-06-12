---
title: "Remapping Mouse Keys"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Nesagwa on 2006-07-02
Ok, Im using Xubuntu 6.06 and have a Microsoft Explorer 4.0 USB mouse.

A while ago the Left click button started to not pick up clicks very consistantly to the point that I switch the Left Click to the Right button and Right Click to one of the Side buttons.

That was no big deal in windows because of the mouse config program that came with it.

Now Im not sure what to do in Xubuntu.  The mouse config program doesnt let you choose which buttons do what and I cant find much info on how to configure them manually.

I know I can do this with xmodmap, but I have no idea how to use it.

---

### Post by NT4usB on 2006-07-02
There is another way to do it without xmodmap.
[https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons]("https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons")
Back up xorg.conf before you try this.
Be sure you understand how to edit files from a command line. I use vi to edit.
If you break xorg, you'll be looking at a black screen with a cursor.
Play with the numbers until you find the button actions you're after.
You have to restart x each time (ctrl+alt+backspace) to apply the changes. Sometimes a full restart is required when ctrl+alt+backspace doesn't pick up the changes but you know it should work...

type xev in a terminal will let you see what 'numbers' the buttons do when you click in the box.

ed: speling

---

