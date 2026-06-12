---
title: "Fancy menu for GRUB EFI"
date: 2009-08-24
forum: Apple Hardware Users
---

### Post by bean123 on 2009-08-24
Hi,

This is based on Colin's fancy menu patch, with my latest fb driver that provides graphics mode for efi.

Binary package:
[http://grub4dos.sourceforge.net/gfxmenu.zip](http://grub4dos.sourceforge.net/gfxmenu.zip)

Just extract the files to the root directory, and select grub64.efi from rEFIt boot menu. It's a little slow, but the menu looks much better than the original.

There are four themes in grub.cfg, you can use # to comment out the ones you don't want, the default theme is winter.

Here are some screen shot from Colin's project page:
[http://grub.gibibit.com/Themes](http://grub.gibibit.com/Themes)

Source code can be downloaded from my github branch at:
[http://github.com/bean123/grub/](http://github.com/bean123/grub/)

---

### Post by kosumi68 on 2009-08-24
Cool menus, but I can't seem to get it to work on my setup. Where is grub64.efi looking for the fonts and themes? On the same partition, relative to any particular directory, or something else?

---

### Post by pxwpxw on 2009-08-24
Placed in the OSX partition root /
```

/boot/
grub64.efi
grub.cfg

```

Nice first screen, promises great stuff, then getting lost.

Gets the initial graphical boot screen, then 'c' gets nice black window  and shell prompt sh:grub>
(with painfully slow response).

No success so far trying to edit menuentry for actual boot, dont know why.
e.g. could not use 'configfile /grub2.cfg' to get sub-menu.
Do we need to read about classes?
 
Missing commaands in the demo grub64.efi include 'echo' 'read' 'videotest' so selections from first screen fail on these.

Will try more later.

---

### Post by bean123 on 2009-08-25
> **pxwpxw said:**
> Placed in the OSX partition root /
```

/boot/
grub64.efi
grub.cfg

```

Nice first screen, promises great stuff, then getting lost.

Gets the initial graphical boot screen, then 'c' gets nice black window  and shell prompt sh:grub>
(with painfully slow response).

No success so far trying to edit menuentry for actual boot, dont know why.
e.g. could not use 'configfile /grub2.cfg' to get sub-menu.
Do we need to read about classes?
 
Missing commaands in the demo grub64.efi include 'echo' read' 'videotest' so selections from first screen fail on these.

Will try more later.

There are still problem with colin's patch, it's not quite optimized and the screen needs to be redrawn a lot. I plans to rework the menu system soon, this is just a demo of what the fancy menu looks like.

---

### Post by bean123 on 2009-10-17
The new graphic menu system is almost done now, you can use menuentry to add boot items, for example, grub.cfg could be like this:

menuentry "AAA" {
  set root=(hd0,1)
  chainloader +1
}

menuentry "BBB" --class ubuntu {
  true
}

. /menu/menu_efi.cfg

You can also use config file format, which allows you to construct sub menu as well:

menu
{
  Linux
  {
    command = "linuz .. \n initrd .."
  }

  "Sub Menu"
  {
    Halt
    {
      class = "Other"
      command = "halt"
    }

    Reboot
    {
      command = "reboot"
    }
  }
}

Save this to a file like my_menu.txt, then use merge_config to append it to the menu list:

merge_config /my_menu.txt

The menu.cfg file appends a Tools menu, it contains the following tools:

Toggle Mode
Switch between text and graphic mode

Terminal
Open a terminal window, ESC to quit

Change Theme
Change menu theme

Layout Demo
Run the layout demo, ESC to quit

Halt
shutdown

Reboot
reboot

The resource file is at:

[http://grub4dos.sourceforge.net/menu.zip](http://grub4dos.sourceforge.net/menu.zip)

---

### Post by pxwpxw on 2009-10-18
After editing several files to get a working gfx menu I liked, looking good, all OS booting ok. The background picture makes it necessary to tweak terminal background and some other colours. Lots of options to understand.
Terminal is good, still missing history and tab completion, also paging option (like efi shell -b on individual command). Other multiple terminal configurations work well (not popup). 

Screen 1920x1200.

Not tried on text screen, default is too small, refit efi shell can change text mode to max native resolution (mode command), but IDK why one would need to use text mode on Apple.

Attached pictures and detail on edited files.
This was grub.cfg
```

. /menu/pxw1x.cfg
. /menu/menu_efi.cfg

```

---

### Post by bean123 on 2009-10-18
Update:

TAB completion for term.

Support key mapping, for example, you can map F5 to ctrl-x using this:

mapkey {
  f5 = ctrl-x
}

Support user defined hotkey, for example, in the demo:

onkey {
  c = "menu_popup term_window"
  e = "menu_popup edit_window edit.text=command"
  f7 = "menu_popup layout_test"
  f8 = menu_toggle_mode
  f9 = halt
  f10 = reboot
}

c open a terminal window, e open a edit box to edit the current
command, use ctrl-x to save it. f7 runs the layout demo test, f8
toggle between text and graphic mode, f9 shutdown, f10 reboot.

Optimize screen update algorithm, the menu should run more smoothly.

The demo file at [http://grub4dos.sourceforge.net/menu.zip](http://grub4dos.sourceforge.net/menu.zip) is updated.

---

### Post by pxwpxw on 2009-10-19
> **bean123 said:**
> Update:

TAB completion for term.

Support key mapping, for example, you can map F5 to ctrl-x using this:

mapkey {
  f5 = ctrl-x
}

Support user defined hotkey, for example, in the demo:

onkey {
  c = "menu_popup term_window"
  e = "menu_popup edit_window edit.text=command"
  f7 = "menu_popup layout_test"
  f8 = menu_toggle_mode
  f9 = halt
  f10 = reboot
}

c open a terminal window, e open a edit box to edit the current
command, use ctrl-x to save it. f7 runs the layout demo test, f8
toggle between text and graphic mode, f9 shutdown, f10 reboot.

Optimize screen update algorithm, the menu should run more smoothly.

The demo file at [http://grub4dos.sourceforge.net/menu.zip](http://grub4dos.sourceforge.net/menu.zip) is updated.

All good so far on IMAC81, aluminium keyboard, 

Terminal TAB completion is great.
(history?).

All works well with all the keys in mapkey, onkey (right from the startup screen), still to checkout editing boot command. (just using your menu and grub64.efi).

terminal scroll back buffer seems to be about 140 lines, seems to also need paging option for long output.

All this with no significant increase in grub64.efi size.

---

### Post by bean123 on 2009-10-19
> **pxwpxw said:**
> 
terminal scroll back buffer seems to be about 140 lines, seems to also need paging option for long output.

This can be configured via max_lines property, for example:

term_window {
  panel {
    class = frame
    width = 100%
    height = 100%
    term {
      width=100%
      height=100%
      max_lines=500
    }
  }
}

You can also set max_lines=0 to indicate infinite history, when output gets too long, use clear command to reset screen.

If max_lines is not set, default value 100 would be used.

---

### Post by pxwpxw on 2009-10-19
Yes max_lines works nicely. gfx terminal is very fast now, but text terminal wins for debuggiing - try set debug=all with command line boot linux /vmlinuz (debian lenny).

---

### Post by pxwpxw on 2009-10-20
Text mode window size and resolution.

On 1920x1200 display (24inch) EFI text mode default is a small window 80 column 25 row, compared with full size  240 row 63 col. The small window also has some problems with displaying the Tools menu.

EFI shell can change this -
```

Shell> mode
 Available modes on standard output
  col 80 row 25 *
  col 80 row 50
  col 240 row 63
Shell> mode 240 63

```

This switches to full screen text mode, giving big improvement for terminal or edit. But it requires commandline booting from the rEFIt efi shell.

Could this selection be made accessible from the grub.efi menu?

---

### Post by bean123 on 2009-10-20
> **pxwpxw said:**
> Text mode window size and resolution.

On 1920x1200 display (24inch) EFI text mode default is a small window 80 column 25 row, compared with full size  240 row 63 col. The small window also has some problems with displaying the Tools menu.

EFI shell can change this -
```

Shell> mode
 Available modes on standard output
  col 80 row 25 *
  col 80 row 50
  col 240 row 63
Shell> mode 240 63

```

This switches to full screen text mode, giving big improvement for terminal or edit. But it requires commandline booting from the rEFIt efi shell.

Could this selection be made accessible from the grub.efi menu?

The grub terminal output doesn't have a function for mode switch, but I can select the maximum mode during startup. This function can be integrated in the next version.

---

### Post by bean123 on 2009-10-20
Update:

Support dialog template, the demo uses this to implement both the e and t hotkey:

e = "menu_edit dialog_edit text=command"
t = "menu_edit dialog_edit text=title\nmenu_refresh"

e edits the command, while t edit the menu title.

Add direction function menu_next_node, menu_prev_node, menu_next_anchor and menu_prev_anchor. This is quite useful when you need to bind them to hotkey. For example, the demo adds two terminal example to Tools menu. Inside terminal, normal navigation key up/down/left/right/tab are all used, so you need to define a hotkey to switch focus. The demo uses f6:

f6 = menu_next_anchor

Smart pop up control. If parent menu is at the bottom of screen, sub menu pops to the top, If parent menu is at the top of screen, sub menu pops to the bottom, etc. This ensures the pop up menu won't be clipped by screen border.

Set maximum text mode in EFI.

---

### Post by pxwpxw on 2009-10-20
That looks very good, dual terminal, full screen text mode, good images.
I will add a picture later.

---

### Post by bean123 on 2009-10-26
The main repository is now moved from github to launchpad, the repository at github is removed to avoid confusion, last commit of git can be found at:

[http://repo.or.cz/w/grub2/bean.git](http://repo.or.cz/w/grub2/bean.git)

The launchpad page for the new repository:

[https://launchpad.net/burg](https://launchpad.net/burg)

BTW, anyone knows how to use launchpad's ppa feature to build binary package ?

---

### Post by pxwpxw on 2009-10-26
> **bean123 said:**
> The main repository is now moved from github to launchpad, the repository at github is removed to avoid confusion, last commit of git can be found at:

[http://repo.or.cz/w/grub2/bean.git](http://repo.or.cz/w/grub2/bean.git)

The launchpad page for the new repository:

[https://launchpad.net/burg](https://launchpad.net/burg)

BTW, anyone knows how to use launchpad's ppa feature to build binary package ?

I am using the new repo now -
 revno 1769
bzr branch [https://code.launchpad.net/~bean123ch/burg/trunk](https://code.launchpad.net/~bean123ch/burg/trunk) 
Note it needs the latest launchpad bzr version (karmic).

I have grub pc bios boot installing ok now and running menu on  Apple Imac from bios boot. Not quite as good as the efi version yet, text is missing from the gfx display.

I don't know about ppa, I suppose you loooked here -
[https://help.launchpad.net/Packaging](https://help.launchpad.net/Packaging)
[https://launchpad.net/~mactel-support](https://launchpad.net/~mactel-support)

---

### Post by bean123 on 2009-10-26
Update for revno 1770:

Support transparent icon.

Support command history in term widget. UP/DOWN move through history, ctrl-p/ctrl-n go back to previous output lines. In EFI, ctrl-p/ctrl-n can't be input but you can use mapkey to map them to one of the function keys. By default, it remembers the last 20 commands, use history property to adjust the number.

Support two menu style. Default style is to show sub menu alongside parent, but you can also shows sub menu full screen. To use the alternative style, edit menu/menu.cfg or menu/menu_efi.cfg, use menu_template1 in menu_create command:

menu_create menu_template1 item_template

Misc bug fixes, this version should display font properly in pc mode.

---

### Post by pxwpxw on 2009-10-27
> **bean123 said:**
> Update for revno 1770:

Support transparent icon.

Support command history in term widget. UP/DOWN move through history, ctrl-p/ctrl-n go back to previous output lines. In EFI, ctrl-p/ctrl-n can't be input but you can use mapkey to map them to one of the function keys. By default, it remembers the last 20 commands, use history property to adjust the number.

Support two menu style. Default style is to show sub menu alongside parent, but you can also shows sub menu full screen. To use the alternative style, edit menu/menu.cfg or menu/menu_efi.cfg, use menu_template1 in menu_create command:

menu_create menu_template1 item_template

Misc bug fixes, this version should display font properly in pc mode.

Tue 27 Oct 2009 
----
revno1770  On Apple imac81. 1920x1200  display.

New feature command history in terminal is good.  It all looks good.
I still have to try all the other features. 
Capability to save information from terminal to a file would be useful.

Display font in pc gfx mode is good now.

-----------------------------------
Some side issues -  

EFI textmode has reverted to a 640x480 window in the 1920x1200 display, 
EFI gfxmode now has to be set gfxmode="1920x1200" not "auto" which worked before.

PC textmode is full screen but 80 column 23 line, big characters like default vga - (not sure it this was the case before the update). May be user controllable somewhere?

PC gfxmode can only be set to 4x3 set of resolutions, 640x480...1600x1200.
Good image but wrong aspect ratio when expanded to fill 1920x1200. A VESA limitation?

----------------------------------

IMO the commandline edit would be better if it could insert a new line, like the grub1.97 commandline console. ( Although it can use ';'or '\n' for same effect and has other advantages).
 
----------------------------------

Since the initial load to burg, I noticed some occasional dead keyboard in pc-bios boot on Apple. This has happened in the straight grub 1.97 boot menu and also in new menu, maybe once in 5 restarts and can be in menu selection or edit. Seen 2 times when toggle back from textmode to gfx.

-----------------------------------

The pc build seems to need the recent 'date' bugfix for efi. 
 pxw@im:~/src/burg/pxw/buildpc$ ./grub-mkimage -d . `cat ../../../memodules3` -o grub.img --prefix='(hd0,6)/grub' 
grub-mkimage: error: unresolved symbol grub_set_datetime

------------------------------------

I have been using preloaded modules for grub64.efi and for grub.img multiboot

grub.efi modules -
 
minicmd part_msdos part_gpt fat ext2 hfsplus ntfs reiserfs xfs iso9660 ls search loopback linux chain reboot halt appleldr help configfile hexdump loadbios fixvideo sh video efi_fb gfxterm font png jpeg coreui loadcfg menucmd test gfxmenu textmenu date

grub.img modules -

minicmd sh normal boot part_gpt ext2 fshelp biosdisk multiboot gzio search extcmd memdisk configfile part_msdos  fat hfsplus ntfs iso9660 ls search linux16 chain reboot  halt help hexdump video gfxterm font png coreui loadcfg menucmd test gfxmenu textmenu vbe

---

### Post by bean123 on 2009-10-27
> **pxwpxw said:**
> Tue 27 Oct 2009 
----
revno1770  On Apple imac81. 1920x1200  display.

New feature command history in terminal is good.  It all looks good.
I still have to try all the other features. 
Capability to save information from terminal to a file would be useful.

Display font in pc gfx mode is good now.

-----------------------------------
Some side issues -  

EFI textmode has reverted to a 640x480 window in the 1920x1200 display, 
EFI gfxmode now has to be set gfxmode="1920x1200" not "auto" which worked before.

Unlike GITHUB, The burg repository is based on official grub tree, not phcoder's branch, so some of phcoder's patch is not applied yet, but you can always use this notion:

set gfxmode=0x0

> 
PC textmode is full screen but 80 column 23 line, big characters like default vga - (not sure it this was the case before the update). May be user controllable somewhere?

The maximum line mode only works for EFI.

> 
PC gfxmode can only be set to 4x3 set of resolutions, 640x480...1600x1200.
Good image but wrong aspect ratio when expanded to fill 1920x1200. A VESA limitation?

You can use vbeinfo command to see what modes are supported by vbe.

> 
IMO the commandline edit would be better if it could insert a new line, like the grub1.97 commandline console. ( Although it can use ';'or '\n' for same effect and has other advantages).
 
----------------------------------

Since the initial load to burg, I noticed some occasional dead keyboard in pc-bios boot on Apple. This has happened in the straight grub 1.97 boot menu and also in new menu, maybe once in 5 restarts and can be in menu selection or edit. Seen 2 times when toggle back from textmode to gfx.

-----------------------------------

The pc build seems to need the recent 'date' bugfix for efi. 
 pxw@im:~/src/burg/pxw/buildpc$ ./grub-mkimage -d . `cat ../../../memodules3` -o grub.img --prefix='(hd0,6)/grub' 
grub-mkimage: error: unresolved symbol grub_set_datetime

Thanks for the tip, I'd take a look at it soon.

---

### Post by bean123 on 2009-10-27
Update:

Support password dialog

First, you need to set user and password in grub.cfg, for example:

set superusers=admin
password admin admin
password user user

This defines two users, admin is a super user.

To set authorized users for a boot menu defined with menuentry:

```

menuentry "AA" --users user {
  true
}

```

To set authorized users for a boot item defined using menu section:

```

menu {  
  "AA"  {
    users = user
    command = true
  }
}

```

In onkey section, you can add * at the beginning of a command, this indicates the hotkey can only be used by super users, for example:

```

onkey {
  e = "*menu_edit dialog_edit text=command"
  c = "*menu_popup term_window"
}

```

BTW, this version should fix the previous bug of not enable maximum text mode in EFI and grub_set_datetime not resolved in pc mode.

---

### Post by pxwpxw on 2009-10-28
burg revno1771

That is very good now, must be nearly complete. 
I compiled for grub.efi and pc bios grub.img  (multiboot from grub1.97).  Even have the menu demo running on an old pc celeron700 with 1200x1024 lcd, using grub.img booted from grub0.97 commandline using grub> 'kernel /grub.img' . There are still some things I have to try, password etc.

efi - all looks good, gfx and textmode full 1920x1200

pc -  gfx is limited to 1600x1200 max res shown by vbeinfo, but looks fine, background pictures are sized to fit display, its only 32x32 (or n*n ) icons that get stretched.
And date is fixed thanks.

There is still the occasional keyboard hangup bug in pc boot, I can not reproduce it even  when I try random keying and continuous switching between terminals, quite unpredictable, occurs sometimes before menu demo starts, and requires hard restart. It maybe this Imac. No problem with efi.

There seems to be a lot of potential (pc) interest from the Karmic testing forum in a successor to gfxmenu -
GRUB2 Theming - [http://ubuntuforums.org/showthread.php?p=8178767](http://ubuntuforums.org/showthread.php?p=8178767)
but I expect that forum will close on karmic release 29 Oct.
My grub.img for pc is only 99K, binary could be booted from grub1.97 for people wanting to test on pc.

I wonder how you plan to introduce this for distro use or user configuration?

---

### Post by bean123 on 2009-10-28
Update:

Support savedefault.

Variable savedefault set the system default value. If savedefault=1, save the current boot item.

You can also overwrite the default value for individual items, in menuentry statement --save option always save this item, and --nosave never save the item. If neither --save nor --nosave is specified, the system default in savedefault variable is checked.

In the menu section, use property save=1 or save=0 to achieve the same effect as --save and --nosave.

You also need to set the environment file, default value is ${prefix}/env, you can also use envfile variable to overwrite it.

Support timeout

Use timeout variable to control auto boot. For example:

set timeout=5

it would boot the default item if no key is pressed in 5 seconds. If timeout=0, boot the default item immediately, although you can press a key at startup to halt the auto boot. If timeout is not set, auto boot is disabled.

Support progressbar

This works in conjunction with timeout. When a timeout value is set, you can see the process bar at bottom of screen.

As with this version, all feature from grub legacy has been implemented. There is a grub.cfg inside the menu directory that shows some usage:

```

set superusers=admin
password admin admin
password user user

set timeout=5

set envfile=/menu/env
set savedefault=1
load_env

menuentry Item1 --users user --nosave --class image_tools {
  true
}

menuentry Item2 --save --class image_about {
  true
}

. /menu/menu_efi.cfg

```

---

### Post by pxwpxw on 2009-10-29
reminder - d/l the current menu configuration files from [http://grub4dos.sourceforge.net/menu.zip](http://grub4dos.sourceforge.net/menu.zip)

---

### Post by pxwpxw on 2009-10-29
> **bean123 said:**
> Update:

Support savedefault.

Variable savedefault set the system default value. If savedefault=1, save the current boot item.

You can also overwrite the default value for individual items, in menuentry statement --save option always save this item, and --nosave never save the item. If neither --save nor --nosave is specified, the system default in savedefault variable is checked.

In the menu section, use property save=1 or save=0 to achieve the same effect as --save and --nosave.

You also need to set the environment file, default value is ${prefix}/env, you can also use envfile variable to overwrite it.

Support timeout

Use timeout variable to control auto boot. For example:

set timeout=5

it would boot the default item if no key is pressed in 5 seconds. If timeout=0, boot the default item immediately, although you can press a key at startup to halt the auto boot. If timeout is not set, auto boot is disabled.

Support progressbar

This works in conjunction with timeout. When a timeout value is set, you can see the process bar at bottom of screen.

As with this version, all feature from grub legacy has been implemented. There is a grub.cfg inside the menu directory that shows some usage:

```

set superusers=admin
password admin admin
password user user

set timeout=5

set envfile=/menu/env
set savedefault=1
load_env

menuentry Item1 --users user --nosave --class image_tools {
  true
}

menuentry Item2 --save --class image_about {
  true
}

. /menu/menu_efi.cfg

```

The attached binary seems to be missing modules  password.mod and loadenv.mod and maybe true.mod. 

Compiled from current burg trunk revno 1772 looks ok with this preloaded module list (maybe some not needed). 


minicmd part_msdos part_gpt fat ext2 hfsplus ntfs reiserfs xfs iso9660 ls search loopback linux chain reboot halt appleldr help configfile hexdump loadbios fixvideo sh video efi_fb gfxterm font png jpeg coreui loadcfg menucmd test gfxmenu textmenu date  loadenv password true

I added loadenv password true to my previous list.

Password works for tools, now to try the other features.

Thu 29 Oct 2009 22:37:31.

---

### Post by pxwpxw on 2009-10-29
All working, password, savedefault, progress bar, timeout.
Also with high quality  background picture, the display is very good, but my camera has problems with moire and color from LCD display.

For the different theme selections, some common class group would save having to repeat in every theme ( example the OS classes for OS icons if these are the same in all themes).

attach pix

---

### Post by bean123 on 2009-10-30
Update:

Support enter key in edit. You can use enter key to break a line into two. Use backspace at the beginning of a line to join two lines into one.

Support md5 password. Use utility grub-mkpasswd to generate md5 password, for example:

grub-mkpasswd admin

Output:
$1$A1tpOB3$bTHEMeIVvBbQsLZIWmJp/.

The use this in grub.cfg:

password --md5 admin '$1$A1tpOB3$bTHEMeIVvBbQsLZIWmJp/.'

Don't forget the '' otherwise $ would be used to expand variable.

---

### Post by pxwpxw on 2009-10-30
That looks ok, built grub64.efi from revno1773.

Tried md5 password ok, grub-mkpasswd has to be run in linux, I don't know how to do it in OSX.

The editor with newline insertion is very good now, (better than grub1.97 cmdline edit).

EDIT - OSX generate MD5 based BSD password algorithm 1
im81-3:test pxw$ openssl passwd -1 -salt 1234567 admin
$1$1234567$ergpnZu0mLdD77Dbmwjpb1

---

### Post by bean123 on 2009-11-01
Update:

Integrate new menu system as menu viewer.
Rename several modules, move common function to lib.mod.
configfile can be used to open sub menu.

Now you can use these command to start new menu in pc mode:

```

set gfxmode="640x480"
set gfxfont="Unifont Regular 16"
loadfont /menu/unifont.pf2
insmod vbe
insmod png
insmod coreui
load_config /menu/default.txt

```

default.txt is a minimized theme file, it doesn't depend on other file. You can also replaces it with menu.txt plus blue.txt to see a more advanced sample. (Don't forget to download an updated resource pack at [http://grub4dos.sourceforge.net/menu.zip](http://grub4dos.sourceforge.net/menu.zip))

Without load_config command, it starts the old menu.

To build grub.efi, you can use the following module list:

minicmd part_gpt part_msdos part_apple fat ext2 hfsplus hfs ntfs reiserfs xfs iso9660 udf ls search loopback
linux chain reboot halt appleldr help configfile hexdump loadbios memrw fixvideo crc sh video efi_fb font png coreui loadcfg gfxrgn txtrgn password true loadenv normal nmenu emenu

nmenu - normal menu system (old menu)
emenu - extended menu system (new menu)
gfxrgn - gfx menu region, previous named gfxmenu
txtrgn - text menu region, previous named textmenu

---

### Post by pxwpxw on 2009-11-02
The post #28 grub64.efi binary still works. The default.txt display is not very exciting, but it does provide all the features for booting, editing and terminals.
A "Help" widget or bar showing the onkey list would make it easier to use.
I ran the pc build, no problems, but have not tested results yet.

Any one else testing?

---

### Post by bean123 on 2009-11-02
I just write a document on the configuration of new menu system:

[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

---

### Post by pxwpxw on 2009-11-03
> **bean123 said:**
> I just write a document on the configuration of new menu system:

[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

That is a good doc, it answers many questions I had. 
Using it now running on burg efi and pc build for Imac81, with added icons and tools using merge_cfg to add classes and extra stuff some taken from the last demo menu, post #28. Started from the default.txt config and added bits.

---

### Post by GoldenCrystal on 2009-11-11
Hello,

I have to thank you all for your work on GRUB, allowing me to boot my Macbook in much better conditions than a plain text mode :D
I was still a bit sad, seing that there were not yet any real theme to use, so, based on your example menu, I was able to make a rEFIt-like menu for GRUB2, thus replacing the real rEFIt, which became unusable for me when I wanted to cleanly boot linux in EFI mode.

Right now I don't know what would be a better place to do this, so allow me me give my little contribution here: [rEFIt_Styled_Menu_beta.zip]("http://www.mirari.fr/XpYP")

Currently, I use Gentoo, so I also made an ebuild for BURG, hosted on bugs.gentoo.org for now.
But rest assured I still took care of including a lot of different icons in my theme, so that it can be of use to a lot of people. ;)

By the way, do you know if it would be possible to disable the "Welcome to GRUB" message at boot, or even better, how to leave the EFI graphics untouched at the beginning ? I've not yet taken the time to look at the GRUB source code, so I have no idea of how complex/easy this might be, but such a thing would be great for users like me.

Anyway, thank you very much for letting all of this happen. :)

---

### Post by bean123 on 2009-11-11
> **GoldenCrystal said:**
> Hello,

I have to thank you all for your work on GRUB, allowing me to boot my Macbook in much better conditions than a plain text mode :D
I was still a bit sad, seing that there were not yet any real theme to use, so, based on your example menu, I was able to make a rEFIt-like menu for GRUB2, thus replacing the real rEFIt, which became unusable for me when I wanted to cleanly boot linux in EFI mode.

Right now I don't know what would be a better place to do this, so allow me me give my little contribution here: [rEFIt_Styled_Menu_beta.zip]("http://www.mirari.fr/XpYP")

Currently, I use Gentoo, so I also made an ebuild for BURG, hosted on bugs.gentoo.org for now.
But rest assured I still took care of including a lot of different icons in my theme, so that it can be of use to a lot of people. ;)

By the way, do you know if it would be possible to disable the "Welcome to GRUB" message at boot, or even better, how to leave the EFI graphics untouched at the beginning ? I've not yet taken the time to look at the GRUB source code, so I have no idea of how complex/easy this might be, but such a thing would be great for users like me.

Anyway, thank you very much for letting all of this happen. :)

Thanks a lot for your support. BTW, I have created three themes based on Colin's menu demo. It can be downloaded at:

[http://grub4dos.sourceforge.net/themes.tar.bz2](http://grub4dos.sourceforge.net/themes.tar.bz2)

Extract it to root directory, theme files should be in /boot/grub/themes/.

To enable in in EFI, add these lines at the end of grub.cfg:

```

set gfxmode="0x0"
set gfxfont="Unifont Regular 16"
loadfont /boot/grub/themes/fonts/unifont.pf2
loadfont /boot/grub/themes/fonts/aqui.pf2
loadfont /boot/grub/themes/fonts/edges.pf2
loadfont /boot/grub/themes/fonts/lime.pf2
loadfont /boot/grub/themes/fonts/7x13B.pf2
loadfont /boot/grub/themes/fonts/smoothansi.pf2
loadfont /boot/grub/themes/fonts/Helvetica-Bold-14.pf2
load_config /boot/grub/themes/proto/theme.txt

```

To enable in in PC mode, add these lines at the end of grub.cfg:

```

set gfxmode="640x480"
insmod vbe
insmod png
insmod coreui
set gfxfont="Unifont Regular 16"
loadfont /boot/grub/themes/fonts/unifont.pf2
loadfont /boot/grub/themes/fonts/aqui.pf2
loadfont /boot/grub/themes/fonts/edges.pf2
loadfont /boot/grub/themes/fonts/lime.pf2
loadfont /boot/grub/themes/fonts/7x13B.pf2
loadfont /boot/grub/themes/fonts/smoothansi.pf2
loadfont /boot/grub/themes/fonts/Helvetica-Bold-14.pf2
load_config /boot/grub/themes/proto/theme.txt

```

The last line is the theme file to load, there are three themes available.

proto: /boot/grub/themes/proto/theme.txt
ubuntu: /boot/grub/themes/ubuntu/theme.txt
winter: /boot/grub/themes/winter/theme.txt

Here are some screenshots:

---

### Post by bean123 on 2009-11-11
PPA package available, detail information can be found at:

[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

---

### Post by bean123 on 2009-11-17
Create a new team in launchpad:

[https://launchpad.net/~burg](https://launchpad.net/~burg)

It's open, anyone can join in. Team mailing list:

[email]burg@lists.launchpad.net[/email]

---

### Post by bean123 on 2009-11-18
> **bean123 said:**
> Create a new team in launchpad:

[https://launchpad.net/~burg](https://launchpad.net/~burg)

It's open, anyone can join in. Team mailing list:

[email]burg@lists.launchpad.net[/email]

Oh, I think google groups is more easy to use and manage, therefore
the mailing list is moved to:

Group home page: [http://groups.google.com/group/burg-devel](http://groups.google.com/group/burg-devel)
Group email address: [email]burg-devel@googlegroups.com[/email]

---

### Post by davibe on 2009-12-01
was anyone able to boot an USB ubuntu installation using a mac ??

---

### Post by L_V on 2011-01-11
-

---

### Post by bilallucky on 2011-01-11
Support dialog template, the demo uses this to implement both the e and t hotkey:

e = "menu_edit dialog_edit text=command"
t = "menu_edit dialog_edit text=title\nmenu_refresh"

e edits the command, while t edit the menu title.

Add direction function menu_next_node, menu_prev_node, menu_next_anchor  and menu_prev_anchor. This is quite useful when you need to bind them to  hotkey. For example, the demo adds two terminal example to Tools menu.  Inside terminal, normal navigation key up/down/left/right/tab are all  used, so you need to define a hotkey to switch focus. The demo uses f6:

f6 = menu_next_anchor

Smart pop up control. If parent menu is at the bottom of screen, sub  menu pops to the top, If parent menu is at the top of screen, sub menu  pops to the bottom, etc. This ensures the pop up menu won't be clipped  by screen border.

---

