---
title: "keys z to b deactivated"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by steve82 on 2007-03-07
hi, i am new to ubuntu. please help. (sort of urgent)

i tried to configure keyboard shortuts, making keys z to b (+Ctrl & Shift) play, stop, forward, and so on, for media playing. 

actually, 2 problems:

1. it didn't work for any of the pre-installed media players.

2. now my z, x, c, v, b keys do not respond. i am using the character map to type this. (otherwise it would look like this: "now my , , , , ,  keys do not respond. i am using the harater map...")

i tried to fix it by reverting the keyoard shortuts, but that didn't work. zxcvb still don't respond. 

any suggestions?

thanks a lot

-stee

---

### Post by jfinkels on 2007-03-08
I'm no expert but here's some information you can use as a starting point:

[LIST=1]
[*]Install the program "xmodmap", if it's not already installed:
```
sudo aptitude install xmodmap
```
For more information about xmodmap visit this site ([http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html]("http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html")) or type the following:
```
man xmodmap
```
[*]To view all your keymappings, type the following (use your up and down arrow keys to scroll through the list and press the <q> key to quit the "less" program):
```
xmodmap -pke | less
```
On my computer, the <zxcvbnm> range is from keycode 52 to keycode 58. Yours should be similar.
[*]To change the mapping of a key to a keycode, type the following command:
```
xmodmap -e 'keycode *##* = *key* *shiftkey*'
```
where *##* is a one, two, or three digit number representing the keycode, *key* is what the key does on your keyboard when you press it, and *shiftkey* is what the key does when you press it in conjuction with the <shift> key. So if I wanted to change keycode 52 to represent <z> and <Z> I would type the following:
```
xmodmap -e 'keycode 52 = z Z'
```
Of course, if your keycodes are already bound correctly, then I don't know how to fix your problem :).
[*]This is the website that I started at when I was changing the multimedia keys on my laptop ([http://rtr.ca/dell_i9300/)]("http://rtr.ca/dell_i9300/"). You most likely have a different computer, but the idea is the same. If you scroll down about three quarters of the page, there's a bullet point that starts with "To get the Front Panel media buttons working[...]" which includes a script showing a mapping of the keycodes for the front panel media buttons on my own computer to <XF86*> commands (which control volume up and down, play, stop, etc.). I assume you can use similar XF86 commands if you find out the keycodes for your own multimedia buttons. One way to do this is to use the <xev> program. To use this, type the following:
```
xev
```
and then press and release the button whose information you want to see. There's a lot of other goofy info about each button press which I (and probably you) have no use for. However, xev will show you the keycode for most of your button presses (it's in there, just look carefully). You can then use that keycode to map an XF86 command to it using xmodmap as above. (I don't know much about XF86 stuff so I can't really help you beyond this).
[/LIST]

I hope I could help. Again, I'm no expert, but hopefully this will give you a starting point. Respond if you have any questions.

---

### Post by steve82 on 2007-03-08
hi jfinkels -- thanks for the reply.

actually i solved it on my own though eventually, so i should probably post my solution:

i just went to System -> Preferences -> Keyboard

then the Layouts tab

click Add

go down to US English (or whatever yours is) (for US English, there are several options if you expand the triangle, but i ignored them, i just selected US English and hit OK)

so then there were 2 'Layouts'

'Remove' the old one

you're done.

i also discovered that when i chose my specific keyboard out of the list in that same Layouts menu, i got additional functionality out of the multimedia keys without having to do any extra configuration.

hope this helps anyone with the same prob.

-s

---

### Post by jfinkels on 2007-03-08
well your way is much simpler, i was reinventing the wheel over here :)

---

