---
title: "Right alt key not working"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by android mouse on 2007-04-06
I'm using an hp pavilion dv5000 laptop and my left alt key doesn't seem to be working. I tried to find my keyboard model in System > Preferences > Keyboard but the only thing I found remotely similar was Hewlett-Packard Pavilion ZT11xx and switching to it did not make the left alt key work.

I'm not sure what to do from here. Can someone help me getting this key functional?

thanks

---

### Post by deadgobby on 2007-04-06
Key boards get all sorts of junk loaded in between them. So I would go out and get a can of air and air out all the dust bunnies and crud. 
Gobby

---

### Post by gilforsyth on 2007-04-06
If it's your right alt key that isn't working, there is a known bug about that.  
Open up your /etc/X11/xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
and put a # in front of the line that reads ' Option "XkbOptions" "lv3:ralt_switch" '
Save & Close and then restart X (ctrl alt backspace).

That should fix your right alt key.  If it's your left... then I don't know.

---

### Post by ricardisimo on 2007-04-06
If what you're looking for is third level functions, there's a more GUI way to do this as well: System > Preferences > Keyboard (might be slightly different if you're on Edgy or Dapper... don't know). "Layout Options" tab has a "Third Level Choosers" section. Make sure that both Left Alt and Right Alt are selected.

---

### Post by quickwitt on 2007-04-23
Thanks!

Worked on my Toshiba U205.

I love this community.

---

### Post by srhlefty on 2007-04-23
random comment:  I don't think I've ever pressed my right ALT key before!

---

### Post by amireldor on 2007-11-29
I got an HP dv6000 (actually dv6282ea) and my right alt does not work. I tried the 'third level choosers' trick but it didn't do anything for the right alt and it made the left alt stop working so i'm still looking on how to fix that.

The right alt thing does not work also when i connect an external USB keyboard - does that mean anything?

Also, When i press the right alt on the 'keyboard shortcuts' menu (plus a key) it says "Mod5+<key>" instead of "Alt+<key>". How do i remap this funny Mod5 to a regular alt? :confused:

---

### Post by gilforsyth on 2007-11-30
Try running 
```
xmodmap -pke
``` 
in the terminal and check the output.  
keycode 64 should be left Alt and keycode 113 should be right Alt, but it sounds like your 113 is assigned to something else.  

If it is something else, you can reassign it to function as the right Alt key.  
In a terminal, type:

```
xmodmap -e "keycode 113 = Alt_R"
```

Now run xmodmap -pke again and see if keycode 113 has changed to keycode 113 = Alt_R

You can check the functionality of the Alt key in your browser or whatever.  If it does work you can set it up to run on every reboot. 

To add it to your sessions.

Go to System -> Preferences -> Sessions
Go to the Startup Programs tab
Click 'Add'
Put in xmodmap -e "keycode 113 = Alt_R" and click OK.

Hope that helps.

---

### Post by amireldor on 2007-11-30
thanks for the quick reply!
I tried the xmodmap thing for keycode 113, but it seemed to disable my working alt. I tried all kinds of stuff, but didn't understand what i'm doing.

I ran this if it helps to debug the issue:
```

> xmodmap -pke | grep -i alt

keycode  64 = Alt_L ISO_Prev_Group ISO_Prev_Group NoSymbol ISO_Prev_Group
keycode 113 = ISO_Level3_Shift ISO_Next_Group
keycode 125 = NoSymbol Alt_L

```
[SIZE="1"][COLOR="Silver"](i think that's what originally was there, the output was a bit different after i played with xmodmap and was too lazy to restart x)[/COLOR][/SIZE]

How can I check which keycode is the key I press?

---

### Post by gilforsyth on 2007-11-30
I think if you run 'xev' in terminal you can check your outputs.  
You might also try 
xmodmap -e "keycode 113 = Alt_R Meta_R"

I don't remember how I fixed this on my machine when I was running feisty...
Bit of a pain, but you can always check out a gutsy livecd and see if it's fixed.  I didn't have to workaround when I upgraded.

---

### Post by ianfp on 2007-12-08
Running the following command worked for me:

xmodmap -e "keycode 113 = Alt_L ISO_Prev_Group ISO_Prev_Group NoSymbol ISO_Prev_Group"


Put it in your .bash_profile or .bashrc to make it happen every time.

---

