---
title: "[SOLVED] Tomboy notes stoped working"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Marc Hoffman on 2007-09-19
Tomboy notes will no longer open. I have tried to remove and reinstall but with no luck. Using terminal to open tomboy i get the following output:

[DEBUG]: NoteManager created with note path "/home/marc/.tomboy".
Trying Plugin: Backlinks.dll ... BacklinksPlugin. [DEBUG]: Done.
Trying Plugin: Bugzilla.dll ... BugzillaPlugin. [DEBUG]: Done.
Trying Plugin: Evolution.dll ... EvolutionPlugin. [DEBUG]: Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. [DEBUG]: Done.
Trying Plugin: FixedWidth.dll ... FixedWidthPlugin. [DEBUG]: Done.
Trying Plugin: NoteOfTheDay.dll ... NoteOfTheDayPlugin. [DEBUG]: Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. [DEBUG]: Done.
Trying Plugin: StickyNoteImport.dll ... StickyNoteImporter. [DEBUG]: Done.
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG]: Tomboy remote control active.
[DEBUG]: EnableDisable Called: enabling... True
[DEBUG]: Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG]: Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

Unhandled Exception: System.ArgumentOutOfRangeException: Argument is out of range.
Parameter name: startIndex
at System.String.Substring (int) <0x000cb>
at NoteOfTheDay.GetContentWithoutTitle (string) <0x0002a>
at NoteOfTheDay.HasChanged (Tomboy.Note) <0x00071>
at NoteOfTheDay.CleanupOld (Tomboy.NoteManager) <0x00286>
at NoteOfTheDayPlugin.CheckNewDay (object,System.EventArgs) <0x00075>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_object_EventArgs (object,System.EventArgs) <0x0003e>
at Tomboy.InterruptableTimeout.TimeoutExpired () <0x00019>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_bool () <0x0002c>
at TimeoutProxy.Handler () <0x0002a>
at (wrapper native-to-managed) TimeoutProxy.Handler () <0x00036>
in (unmanaged) 0xb7eea3c5
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Gnome.Program.Run () <0x00007>
at Tomboy.Application.StartMainLoop () <0x00014>
at Tomboy.Tomboy.StartTrayIcon () <0x000b2>
at Tomboy.Tomboy.Main (string[]) <0x001bc>


Any help appreciated.

---

### Post by Marc Hoffman on 2007-09-21
still can't get this to work, can anybody give me a clue please?

---

### Post by Marc Hoffman on 2007-09-22
Are there any Tomboy experts on the boards this evening who could help?

---

### Post by bsmith1051 on 2007-09-28
sorry no one offered to help.  Not sure if I can help either but I'll try.

1. Are you having any other problems with your system, i.e., is it possible that Tomboy failing to load is a symptom of something besides the Tomboy software?

2. Try deleting (or just renaming) the hidden .tomboy configuration folder.   To do this:
- click on Places > Home Folder
- press CTRL-H to un-hide all the hidden configuration folders (these are all the folders with a dot as the first character in the name)
- locate the .tomboy folder and rename it, e.g. tomboy.old
- try opening Tomboy again.  It should recreate the .tomboy folder and use all default settings

Recreating your config folder will 'lose' your notes but it also might fix the startup problem!  And if you look in the original folder you'll see your notes as text files with weird names, but you can still open them and copy the text.

---

### Post by Marc Hoffman on 2007-09-28
Thanks for the help - back on track now. I tried to copy my old notes into the new folder but this threw up the same error message but deleting them allows tomboy to run- must of wrote something it didn't like.

Marc

---

### Post by bsmith1051 on 2007-09-28
glad I could help!  Don't try to directly 'import' your old notes, i.e., copying the original files into the new folder.  Instead, you should be able to open them as text files.  You'll see XML code (which you can ignore) and then simply copy-and-paste the important stuff from the text-editor window into a new Tomboy note window.

---

