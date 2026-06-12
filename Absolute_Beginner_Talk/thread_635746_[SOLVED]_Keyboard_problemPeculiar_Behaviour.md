---
title: "[SOLVED] Keyboard problem:Peculiar Behaviour"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by spai on 2007-12-09
I have a problem with the keyboard layout(I think so).It behaves strangely, I dont know why,
[U]
Some instances of peculiar behaviour:[/U]

I press : ´ and s[any alphabet will do]
Output:  &#347; (instead of ´s)

I press: Shift and ´
Output: ¨ (instead of ")

I press: x + Shift + ^ + 2
Output: x²(instead of x^2)

I want the usual keyboard configuration. I think while installing gutsy, I erroneously chose this setting. I have seen the keyboard preferences tab. There are tons of options there, and I dont know which is the setting to choose.
Can anyone look at their setting (I mean people who use U.S International English) and tell me?
 
Settings:
[B]In Keyboard Preferences tab,

Keyboard Model: *Generic 105-key (Intl) PC*
Keyboard Model: *U.S.International ¨with dead keys¨*
[/B]
Thank You in advance :)

P.S: If you are wondering how I actually presented what I wanted, I copied it from other sites :(
And the last peculiar behaviour is particularly useful. If someone knows how to retain it while foregoing the remaining problems, that will be great 8)

---

### Post by Kosimo on 2007-12-09
Gutsy have plenty of issues with keyboards, changing layouts etc....

I'm thinking going back to Feisty since Herdy become stable.

---

### Post by spai on 2007-12-09
Whoops, So there is no solution?What a bummer! I really like gutsy:( 
I hope there is a solution to this problem.It will be bad to go back to feisty, for a small problem like this.

---

### Post by greybirds on 2007-12-09
You've got dead keys enabled :) Useful if you type in languages that have the doodly bits above letters, but a real pain in english.

To get back your normal keyboard, do the following:
[LIST=1]
[*]Select System > Preferences > Keyboard
[*]Click the Layouts tab
[*]See if you have "U.S. English" listed under Selected Layouts. If so, click the radio button to the right of it to make it default. That should be it. Close the window and all new applications you open will use the normal US English layout. The ones you had running beforehand might continue to use the old layout until you quit and reopen them.
[*]If "U.S. English" isn't listed, then you want to install it. Click the "Add" button near the bottom of the window. A big window with a keyboard diagram will open up.
[*]In the first drop-down box, click and select "U.S. English" (you'll have to scroll a bit; it's near the bottom)
[*]In the second box, make sure "Default" is selected. The keyboard diagram should look like your standard keyboard layout.
[*]Click the "Add" button. The window with the keyboard closes and takes you back to the keyboard preferences window.
[*]"U.S. English" will now be displayed in the list. Click its radio button to make it default.
[/LIST]

That's it. 

You can also add an applet to your panel that will let you change between all the keyboard layouts you have installed. 
[LIST=2]
[*]Right click on the panel you want to add the applet to and click "Add to Panel"
[*]Find "Keyboard Indicator" (look for an icon with flags) and drag it to where you want it to sit on the panel.
[*]Close the window with the applets palette.
[/LIST]
It should start out with "USA", which is your standard keyboard layout. Click it, and it will cycle through your other layouts. Useful if you're trying to type foreign text. 

You might also be interested in the applet "Character Palette", which lets you quickly copy special characters to the clipboard and paste them into any text you want. 

Hope this helps.

---

### Post by spai on 2007-12-09
It was very detailed, thanks for that.
But I still have that problem,(I logged out and logged back in, still no use)

 ¨  &#347;  x²  --------- See? Not yet gone!
I tried all,Defaults,  Macintosh, Dvorak, Alternative in the options.... but none of them work!
Interestingly the keyboard pic there, does not show this [SIZE="5"]¨[/SIZE] , yet it appears when I type.

> You might also be interested in the applet "Character Palette", which lets you quickly copy special characters to the clipboard and paste them into any text you want.

Thanks for that info. It helps a lot :)

---

### Post by greybirds on 2007-12-09
Well, in the meantime, you can work around the weirdness by typing the punctuation key twice (type ' ' s to get 's). 

I guess my first step is to make certain the new layout is being activated. Installing it doesn't make it the active one; make sure the correct radio button in the right column of the layout list is selected.

Beyond that, try removing all the layouts except the default US English one. With only one in the list, it will have to activate it.

If that doesn't work, there may be some other service that's implementing dead keys that I'm not familiar with. Do you remember installing anything having to do with foreign languages or keyboard layouts?

---

### Post by spai on 2007-12-09
Ahh finally, removing all others worked \\:D/
I had actually checked the radio button, but it was not working.

[COLOR="Red"]"[/COLOR]Thank you[COLOR="Red"]"[/COLOR] **greybirds**, it[COLOR="Red"]'[/COLOR]s working now ;)

---

