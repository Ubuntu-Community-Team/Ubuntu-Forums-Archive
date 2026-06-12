---
title: "Cannot find/start prog"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-05-05
I downloaded and installed, through synaptic, a media prog named Timidity. I can't find it anywhere. No Icon, listing or any trace of it, yet synaptic says that it is installed. Guess I need a command in terminal to bring it up. Already tried app get and timidityfile and the only thing I got was the danged EULA. It didn't have an I agree or ok button. Nothing, nada, zilch.

So my question is, how do I open/bring up this prog.

Many thanks,

Jon

---

### Post by jfinkels on 2007-05-05
> **Romin-1 said:**
> I downloaded and installed, through synaptic, a media prog named Timidity. I can't find it anywhere. No Icon, listing or any trace of it, yet synaptic says that it is installed. Guess I need a command in terminal to bring it up. Already tried app get and timidityfile and the only thing I got was the danged EULA. It didn't have an I agree or ok button. Nothing, nada, zilch.

So my question is, how do I open/bring up this prog.

Many thanks,

Jon

Try typing "timidity" in the terminal. If that works and you really want a shortcut, you can right click on the desktop and create a new launcher.

If that doesn't work, open Synaptic, find the listing for the timidity package, right click and select "Properties..." and then go to "Installed Files".  There will most likely be a file in there in the "/usr/bin/" directory (or very unlikely, the "/usr/local/bin/" directory). Any file in the "/usr/bin" directory is an executable file, and you can run any file in there by simply typing the name of that file at the command prompt.

---

### Post by bobplano on 2007-05-05
why don't you try gksudo so it's not run in the terminal

---

### Post by Romin-1 on 2007-05-05
Thanks many jfinkels but all I got was "cannot find file" or "permission denied".

Thanks to bob plano "BUT" I'm new to this stuff and don't really know how to run gksudo or many other commands as yet.

Is there a page that the most used commends are listed along with what they do?

Thanks again fellows,

Jon

---

### Post by ubromtoo on 2007-05-28
I'm having the same problem with timidity : it just won't show up. typing "timidity" in

the terminal gives me the following:

richard@richard-desktop:~$ timidity
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

richard@richard-desktop:~$


          tried gksudo, same thing.   any ideas?  maybe it's a Dapper bug ?

---

