---
title: "installing dcsharp-0.10.0"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by network.burner on 2007-10-04
i hv downloaded dcsharp-0.10.0.tar.bz2
i dont know how to install it.
please help me out...
plz write the steps  frm beginning as m an absolutely new to ubuntu.


Thanks in advance.

---

### Post by nest on 2007-10-04
> **network.burner said:**
> i hv downloaded dcsharp-0.10.0.tar.bz2
i dont know how to install it.
please help me out...
plz write the steps  frm beginning as m an absolutely new to ubuntu.


Thanks in advance.

1) tar xvfj dcsharp-0.10.0.tar.bz2
2) cd dcsharp-0.10.0
3) ./configure
4) make
5) sudo make install

if you have the libs that dcsharp needs should word perfect.

---

### Post by network.burner on 2007-10-04
when i type ./configure
it gives this error:
bash: ./configure: No such file or directory

---

### Post by nest on 2007-10-04
try [this]("http://ubuntuforums.org/showthread.php?t=28378") ;)

---

### Post by rodgersan on 2007-10-29
install instructions are in the README file.... basically you need scons...

> **nest said:**
> try [this]("http://ubuntuforums.org/showthread.php?t=28378") ;)

Downloaded dcsharp 0.11.1 source and tried to compile it myself but I get this:

```
Thread 1 (Thread -1211152688 (LWP 14802)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7dc1301 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ee1780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7ee1b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7cd3844 in ?? ()
#6  0xb7cd382c in ?? ()
#7  0xb7cd3828 in ?? ()
#8  0xb7cd3824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
```

I have already had that error once with fspot under edgy and resolved it installing a mysterious package related to mono...

I googled it a bit but nothing worked... 

Maybe someone knows?

---

### Post by gubemton on 2007-11-12
rodgersan, please post the full error output from scons. You are probably missing a mono package, maybe libmono-cairo2.0-cil.

---

### Post by rodgersan on 2007-11-12
> **gubemton said:**
> rodgersan, please post the full error output from scons. You are probably missing a mono package, maybe libmono-cairo2.0-cil.

thanks gubemton, it worked!

---

### Post by TeePOG on 2008-05-21
Hi all

I do have libmono-cairo2.0-cil installed, as well as all the dependencies mentioned on the project page and the README file.

When I run scons, whether as normal user or with sudo, I get the following error message(s):

gtk/src/Page/PageManagerNotebook.cs(63,33): warning CS0612: `Gtk.Tooltips' is obsolete

gtk/src/HubWindow.cs(125,32): error CS0121: The call is ambiguous between the following methods or properties: `Gtk.TreeViewColumn.SetCellDataFunc(Gtk.CellRenderer, Gtk.CellLayoutDataFunc)' and `Gtk.TreeViewColumn.SetCellDataFunc(Gtk.CellRenderer, Gtk.TreeCellDataFunc)'

/usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous error)

/usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous error)

gtk/src/HubWindow.cs(130,32): error CS0121: The call is ambiguous between the following methods or properties: `Gtk.TreeViewColumn.SetCellDataFunc(Gtk.CellRenderer, Gtk.CellLayoutDataFunc)' and `Gtk.TreeViewColumn.SetCellDataFunc(Gtk.CellRenderer, Gtk.TreeCellDataFunc)'

/usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous error)

/usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous error)

gtk/src/ConnectionStatusbar.cs(54,40): warning CS0612: `Gtk.Tooltips' is obsolete

gtk/src/General/VisibleColumnsWindow.cs(72,32): error CS0121: The call is ambiguous between the following methods or properties: `Gtk.TreeViewColumn.SetCellDataFunc(Gtk.CellRenderer, Gtk.CellLayoutDataFunc)' and `Gtk.TreeViewColumn.SetCellDataFunc(Gtk.CellRenderer, Gtk.TreeCellDataFunc)'

<snip more of the same>

What do I still need to do to compile this?

---

