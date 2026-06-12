---
title: "Timidity installed but can't run"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-22
I recently installed timidity by doing sudo apt-get install timidity. I do not know how to find it or run it but I did find a timidity file in my /etc but it has no executable. I would greatly appreciate if you could give me some pointers on how to find an run timidity and possibly add it to one of my menus. Thank you.

:popcorn:

---

### Post by mikewhatever on 2007-02-22
Usually, typing timidity in the terminal or in the window that opens by Alt+F2, will launch the program. If also seems that > which timidity will find an executable, and > locate timidity will give an the list of all files associated.

---

### Post by jprb85 on 2007-02-22
I have done both but for some reason Timidity will not load. I know that I installed it correctly though. Do you have any more advice so that I can run timidity?

:lolflag:

---

### Post by Maestro23 on 2007-02-22
> **jprb85 said:**
> I have done both but for some reason Timidity will not load. I know that I installed it correctly though. Do you have any more advice so that I can run timidity?

:lolflag:

I don't use the program myself, but I took a look at the install doc.

Did you read the INSTALL doc and do all 4 steps like it said.

---

### Post by Ashimura on 2008-02-24
I'm having the same problem.

This is basically what happens:
```
:~$ timidity
TiMidity++ version 2.13.2 -- MIDI to WAVE converter and player
Copyright (C) 1999-2004 Masanao Izumo <iz@onicos.co.jp>
Copyright (C) 1995 Tuukka Toivonen <tt@cgs.fi>

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA

```After typing this in, all this text shows up, but nothing else happens.

```
:~$ timidity -iA
/usr/local/share/timidity/timidity.cfg: No such file or directory
Interface `A' is not compiled in.
timidity: Can't read any configuration file.
Please check /usr/local/share/timidity/timidity.cfg
```
This part I don't understand. There is no usr/local/share/timidity folder, but the config file is in etc/timidity and the executable is in usr/share/app-install/desktop/. Did something go wrong during installation? =/

---

