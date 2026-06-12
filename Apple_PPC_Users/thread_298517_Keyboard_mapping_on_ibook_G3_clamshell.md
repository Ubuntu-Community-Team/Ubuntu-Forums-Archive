---
title: "Keyboard mapping on ibook G3 clamshell"
date: 2006-11-12
forum: Apple PPC Users
---

### Post by EvanPMeth on 2006-11-12
I currently installed dapper server edition on my apple ibook g3. But for the life of me i can not get the keyboard to properly map the keys. All the leters and numbers along with the arrows and function keys are mapped properly. but the character keys such as the _+{}|:"<>?-=[]\;',./ are all mixed up and random.

Does anyone know the proper keyboard layout for the ibook g3 clamshell and how to change it? I am not running a desktop, because i am not fond of desktop enviroments on slow computers. 

Another question is how do i stop the terminal beeping when at the end of a line, when using arrows.

thanks
-evan

---

### Post by gnomeza on 2006-11-13
Changing the keymap is:
```
sudo dpkg-reconfigure console-setup
```

As for which keymap to use, well, if you don't find one that works, making a custom console keymap isn't too arduous.

OTOH, as a recent Gentoo migrant, I haven't yet worked out how to get my custom keymap loaded on startup. Hints anyone?

---

### Post by EvanPMeth on 2006-11-13
thanks for the help

The correct map when using reconfigure is 
```
pc / qwerty/ US american / Apple USB / Standard
```
when selected from the full list.

I also found this key map which works perfect :
```
# Macintosh us.map
keymaps 0-6,8-9,12
alt_is_meta
include "qwerty-layout"
include "linux-with-alt-and-altgr"
strings as usual
compose as usual for "iso-8859-1" 

keycode   1 = Escape
keycode   2 = one              exclam           exclamdown
keycode   3 = two              at               at
	control	keycode   3 = nul
	shift	control	keycode   3 = nul
keycode   4 = three            numbersign 
	control	keycode   4 = Escape
keycode   5 = four             dollar           dollar
	control	keycode   5 = Control_backslash
	shift	control	keycode   5 = Control_backslash
keycode   6 = five             percent 
	control	keycode   6 = Control_bracketright
keycode   7 = six              asciicircum
	control	keycode   7 = Control_asciicircum
keycode   8 = seven            ampersand        braceleft
	control	keycode   8 = Control_underscore 
keycode   9 = eight            asterisk         bracketleft
	control	keycode   9 = Delete
keycode  10 = nine             parenleft        bracketright
keycode  11 = zero             parenright       braceright 
keycode  12 = minus            underscore       backslash
	control	keycode  12 = Control_underscore
	shift	control	keycode  12 = Control_underscore
keycode  13 = equal            plus
keycode  14 = Delete           Remove 
	control	keycode  14 = Remove
	shift	alt	keycode  14 = Meta_Delete
keycode  15 = Tab              Tab
keycode  26 = bracketleft      braceleft
	control	keycode  26 = Escape
keycode  27 = bracketright     braceright       asciitilde 
	control	keycode  27 = Control_bracketright
keycode  28 = Return
	alt	keycode  28 = Meta_Control_m
keycode  29 = Control
keycode  39 = semicolon        colon
keycode  40 = apostrophe       quotedbl
	control	keycode  40 = Control_g 
keycode  41 = grave            asciitilde
	control	keycode  41 = nul
keycode  42 = Shift
keycode  43 = backslash        bar
	control	keycode  43 = Control_backslash
keycode  51 = comma            less             guillemotleft 
keycode  52 = period           greater          guillemotright
	control	keycode  52 = Compose
keycode  53 = slash            question         questiondown
	control	keycode  53 = Delete
	shift	control	keycode  53 = Delete 
keycode  54 = Shift
keycode  56 = Alt # Alt/Option key left
keycode  57 = space            space            nobreakspace
	control	keycode  57 = nul
keycode  58 = Caps_Lock
keycode  70 = Scroll_Lock      Show_Memory      Show_Registers 
	control	keycode  70 = Show_State
keycode  83 = KP_Period
	control	alt	keycode  83 = Boot

keycode 101 = Pause # Break/Pause
	control	keycode 101 = Break # Ctrl+Break/Pause

# Apple portables fn key + Apple logo key 
keycode 116 = Compose
# Apple keypad has equal
keycode 117 = equal

# Apple logo keys
keycode 125 = VoidSymbol # left Command/Apple key
keycode 126 = Compose # right Command/Apple key
```

The last line will have to be deleted for ibook g3 clamshells but i believe it works with powerbooks and ibooks(non clamshell)

To get a map to load as default the only way i can think of is to add this line too your /etc/rc.local
```
exec loadkeys /path/to/key.map
```
-Evan

---

### Post by Gen2ly on 2007-12-20
Nice research EvanPMeth.  This is just what I needed.  Actually these are the mappings for xorg-server.  To use em just put them in xorg.conf:

        Option          "XkbLayout"     "us"
        Option          "XkbModel"      "macintosh"

---

