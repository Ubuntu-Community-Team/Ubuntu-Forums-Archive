---
title: "Counter strike source + Wine cant change graphics"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by andreasoz on 2007-08-10
Hello!

I have successfully installed wine and I can launch Counter strike source from steam. However, I cannot change the graphic in video option. 

I am stuck with medium to low graphic. When I try to change the graphic CSS just crash. Would be nice if someone could help me with this.

Thanks

---

### Post by Hospadar on 2007-08-10
Most of those options can be set at runtime via command line options and wine generally has troube resetting graphics in-game like that.
some of the options you might look into are -novid (disables opening videos) -h<number> -w<number> (allows you to set resolution at startup time.

Check out this page for a fuller set of options
[http://developer.valvesoftware.com/wiki/Command_Line_Options](http://developer.valvesoftware.com/wiki/Command_Line_Options)

you can add these options to the launcher on the desktop if you want. right click on it, go to Properties->Launcher->Command and append the options to the end of the field as they would appear if you typed them in the terminal.

And seriously, why play CS at all when there are so many good [fps]("http://en.wikipedia.org/wiki/List_of_free_first-person_shooters") for linux =)

---

### Post by andreasoz on 2007-08-10
None of those commands help me with increasing the texture detail etc. 
I can change the resoultion ingame but nothing else.
Isnt there a file where all video options steam use is  that i can edit?

---

### Post by ubuntuforums on 2007-08-10
Just like in windoze you can customize your CSS settings with an autoexec.  Make your new "autoexec.cfg" file here:  \counter-strike source\cstrike\cfg\

Do some googling, you'll find just what you need.  ;)  Now hopefully this will allow you to customize your graphics settings without crashing the game as it will load before going into the game.  Be sure you have your proper gfx driver.

---

