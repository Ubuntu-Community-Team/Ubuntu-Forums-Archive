---
title: "Help - 6 Key input for blind users"
date: 2007-04-27
forum: Assistive Technology &amp; Accessibility
---

### Post by TabletGuy on 2007-04-27
Hi all,

I am trying to set up a PC for visually impaired users at a nearby school.

The users have previously used a 6-key entry system on their standard 101 key keyboard but I cannot figure out how to map a standard keyboard to allow six key entry.

Is anyone able to help with how I can change the keyboard layout to allow six key entry.

(six key entry is allows the user to type any character using a combination of 6 keys of the keyboard).

Thanks,

---

### Post by jaustin19 on 2007-04-29
I'm not familiar with the six key details, but Gnopernicus is a screen reader under Gnome, which offers magnification and speech.  Gnopernicus uses the Ten key pad with various combinations of  keys and layers to gain a multitude of functions for speech.  In comparison to six keys doing what you say it is extreme over-kill, but similar to Jaws and Window-eyes for windoz.  My problem is it works after you  have booted the system then call it via Gnome accessability screens, logout and login,  where as a blind person needs it to come up talking without entervention.  Any suggestions are appreciated

---

### Post by TabletGuy on 2007-04-30
Hi

Thanks for your message. Sorry I can't help you with the setup for Gnopernicus as I am trying to make a solution for a specific situation.

The students in the past have used perkyduck and JAWS to type messages but this system is broken.

PerkyDuck provided the six key entry and JAWS read back the entry to the user.

PerkyDuck will work under WINE but I cannot make either Orca or Gnopernicus read back the text which is written. Orca will read back text entered into gedit but then I need to try to get six key entry working for gedit, hence my original post.

Does anyone know of a six-key entry programme for linux which might be able to be read by Orca or Gnopernicus? or how I can configure a keyboard for six key entry.

Any pointers would be useful - thanks.

---

### Post by Matt Murdock on 2007-05-25
The "six key keyboard" you were referring to is also known as a braille keyboard. It is most commonly used with Personal Note Takers for the blind, but I haven't heard much of them used with PCs. After doing a little Googling (not very much mind you, but I just got started) I have found that you can order Braille Keyboards that will plug into PCs, with software installation. I haven't found anything yet on turning a normal keyboard into a braille one, but almost all of the the plug and play keyboards are based on Linux programming, and some even have a self contained OS in them. I am sure with enough checking, you can find software (if you already have the keyboards) to make them work with Ubuntu. If you have the keyboards, you can also try checking with the manufacturer to see if they have Linux based drivers. Hope that helps a little.

---

### Post by TabletGuy on 2007-05-27
Thanks for your message. In the end I have purchased a 'braille in' keyboard which should work in replacement of the standard keyboard. Once it arrives I'll post on its effectiveness.

But at $750 a keyboard (!!!) it would be great if the accessibility people could implement a six key keyboard layout.

---

### Post by jonathonblake on 2007-06-22
[QUOTE=TabletGuy]But at $750 a keyboard (!!!) it would be great if the accessibility people could implement a six key keyboard layout.[/QUOTE]

a) Wouldn't it be cheaper to train the people to use a standard keyboard?  [I'm sorry.  I just don't get why people would rather spend $5K for a PDA that uses a Perkins Keyboard and Braille Display Unit, rather than buying a laptop with a US Keyboard and Braille Display Unit for $3K.

b) I am looking at how to create keyboard drivers, so that a standard keyboard can emulate a Perkins Keyboard.   I have run into the following issues:
1) How are Meta Keys implemented using a standard Perkins Keyboard?
2) Should it map to the Braille Unicode subrange?
3) Should it map to the local patios?

xan

jonathon

---

### Post by frafu on 2007-06-22
Hello, 

Maybe you should consider looking for help on the ubuntu development mailing list and/or the ubuntu development  channel on irc. (or even the accessibility channel on irc).  

That way, you probably will have a better chance of getting help from knowledgeable people.

[mailing lists]("https://lists.ubuntu.com/#Development+Lists")
[irc]("https://help.ubuntu.com/community/InternetRelayChat")

Have a nice day.

---

