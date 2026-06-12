---
title: "[SOLVED] Do ALT code for fonts work in Ubuntu?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by mridkash on 2007-10-06
Recently, I wanted to have icons on my desktop with no text beneath them so in the name field I wanted to add a non breaking space (which is invisible space character) but couldn't do so in gedit or directly in the name field. So I had to make a html file with a &nbsp; in it and copied over the character from firefox to the name field.

I also use some common alt codes like alt+0169(numeric) makes a copyright character.

For a complete list of alt codes see this site [http://www.usefulshortcuts.com/downloads/ALT-Codes.pdf](http://www.usefulshortcuts.com/downloads/ALT-Codes.pdf)

I want to know how to enable that in Ubuntu.


Thanks

---

### Post by FuturePilot on 2007-10-06
Alt+Numberpad doesn't really work in Linux because of the way Linux handles Unicode characters. But there's a nice little app called Gucharmap. Applications>Accessories>Character Map. Click on View and change it to Unicode Block
Then you can browse through all the characters. And there happens to be a Copyright character. [SIZE="2"]©[/SIZE]
Have fun! :)

---

### Post by Fixman on 2007-10-06
Other way is writing on terminal

```
echo -e "\0N"
```
where 'N' is the (octal) numbre to write

---

### Post by mridkash on 2007-10-06
Thanks for your replies, but these soln's are not as convenient as simply typing a shortcut to access.
And still I couldn't find the nbsp character I want.

I searched on google and found a ubuntuforums archive post which says something about Compose Key setting.

> You can either change the keyboard layout to your desired language (note that keys will probably be changed!) or set the compose key (or both). You can do this in System -> Preferences -> Keyboard.

If you set your compose key to the right control key, you can write an é using this combo: Ctrl (the right control) + ', then pressing e. The + means you press both keys together. Or, better yet (so as to avoid mistakes), hold Ctrl and press the corresponding key, then release and press the remaining last key. For an è you would use: Ctrl + `, then e.

I found some reference to it in the ubuntu help center too.

> Compose key position

                      

    The Compose key allows you to combine two keypresses to make a single character. This is used to create an accented character that might not be on your keyboard layout. For example, press the Compose key, then ', then e to obtain e-acute character.

I think it works, but still where to look for a table of what compose keys will do like i experimented with it &#281; &#279; é Ë 

There I found options for third level keys and even fourth level keys, but how to set them?

However I finally got the nbsp to work. Here is the screenshot. Now when I press Shift+Space it enters a nbsp.
[IMG]http://home.mridul.googlepages.com/Screenshot-KeyboardPreferences-1.png[/IMG]

I need more clarification on third level thing, if it enables me to have "my own keys" on top of normal keys then its great!

---

### Post by mridkash on 2007-10-06
Also, I found this website which talks something about alt codes. [http://robitaille.wordpress.com/2007/03/10/whats-your-linux-whine/](http://robitaille.wordpress.com/2007/03/10/whats-your-linux-whine/)

on that site Martijn said
> You can use Ctrl+Shift+U and then type the hexadecimal Unicode code for the letter you want, and press enter (or space). It should give you the character.
 You can look up the codes in gucharmap.
I'm going to try that!

---

### Post by mridkash on 2007-10-06
WOW, it works! And ah so well!

try this, open a text editor and press keys Ctrl+shift+u , a small underlined u will appear, now leave the keys and type 02da, press enter, zap it turns into a degree symbol.

Now, if you want to search for a symbol, simple, go to accessories>character map and press ctrl+f to start search (there is a search menu above too) and enter what you want to search like say degree.
just remember to tick mark the search in details checkbox.

when you find desired symbol, at the bottom left status bar there it shows a code that you have to type to see that symbol.

And I found the nbsp too!
its code is 00a0 
it works in all text fields.
[edit] Another plus thing is that it doesn't require numeric keys to be enabled, i use laptop and numeric keys are difficult to type. \\:D/

---

### Post by FuturePilot on 2007-10-06
You could also click on the character you want in Gucharmap and then click the Copy button. Then just paste it into whatever you want. Much easier than typing in all those character codes.

---

