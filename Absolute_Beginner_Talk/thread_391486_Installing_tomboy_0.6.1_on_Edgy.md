---
title: "Installing tomboy 0.6.1 on Edgy"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by jazzman83 on 2007-03-23
I am trying to install Tomboy 0.6.1 on Edgy and when I run the make command in the terminal am told:


> 
** (/usr/lib/mono/2.0/gmcs.exe:26434): WARNING **: The following assembly referenced from /usr/lib/mono/gac/gdk-sharp/2.10.0.0__35e10195dab3c99f/gdk-sharp.dll could not be loaded:
     Assembly:   Mono.Cairo    (assemblyref_index=2)
     Version:    1.0.5000.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0).


** (/usr/lib/mono/2.0/gmcs.exe:26434): WARNING **: Could not load file or assembly 'Mono.Cairo, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
.
.
.

make[3]: *** [Tomboy.exe] Aborted (core dumped)
make[3]: Leaving directory `/home/brian/Desktop/tomboy-0.6.1/Tomboy'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/brian/Desktop/tomboy-0.6.1/Tomboy'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brian/Desktop/tomboy-0.6.1'
make: *** [all] Error 2

I did run *./configure* first and it went fine.  Unfortunately, this is my very first time trying to compile something from source in Ubuntu.  Do I need a newer version of the Mono runtime?

Thanks for any help.

---

### Post by jazzman83 on 2007-03-23
I figured it out - the mono.cairo library I had was version 1.0 but Tomboy 0.6.1 required Mono.Cairo 2.0 which I got from the repositories.  Everything works fine now.

---

### Post by dpeirce on 2007-03-30
Me, I installed Tomboy from the repository using adept. It ran the first time but the link didn't work. After that it won't run at all. I find I can make it run one time by deleting the ~/.tomboy/ directory, but then it won't run the second time until I delete the .tomboy again.

When I run it in the terminal I get:

.............................................................

dave@r3-mobile:~$ tomboy
NoteManager created with note path "/home/dave/.tomboy".
Trying Plugin: Evolution.dll ... EvolutionPlugin. Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. Done.
Trying Plugin: StickyNoteImport.dll ... StickyNoteImporter. Done.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Tomboy remote control disabled: Name 'com.beatniksoftware.Tomboy' does not exist.
EnableDisable Called: enabling... True
Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'

(Tomboy:19829): libtomboy-WARNING **: Binding '<Alt>F12' failed!

Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

(Tomboy:19829): libtomboy-WARNING **: Binding '<Alt>F11' failed!

............................................................

Any suggestions?

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

---

### Post by dpeirce on 2007-03-31
OK, I kept fooling with it. It's tricky. In case someone else has this same difficulty:

The program actually *IS* running and there's an invisible icon in the system tray. There aren't any real instructions. Home page is [http://www.gnome.org/projects/tomboy/](http://www.gnome.org/projects/tomboy/). 

I don't know why the icon is invisible, but right or left-clicking will get you menus. Click Start Here and the start page comes up. To create a new note, click Start New Note. Or you can enter the new note's title on the start page, then hilight it, and then click Link on the menubar. 

In faith, Dave
[email]dave@christos.cjb.net[/email], [email]dpeirce@christian.net[/email]
Viva Texas

---

