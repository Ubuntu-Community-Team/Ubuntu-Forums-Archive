---
title: "Calling all Eterm or Midnight Commander Experts"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Nythain on 2007-06-15
ok, so im trying to escape this silly notion of panels and icons and all that icky clutter crap

im making wicked process, learned how to display Eterm without borders, titles, transparent, geometries, all that jazz

Figured out how to utilize htop, root-tail, netstat, now im working on Midnight Commander

What im trying to do is always have an eterm blended into my desktop that is running MC all the time
I can get eterm itself to do what i want, but when i run mc in it it displays all funny (see screenshot).
When i run eterm default (usually just using alt+f2 and typing eterm with no arguments) it displays perfectly fine doing exactly what i want it to.

im calling eterm like this
```

Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=144x42+0+76 --font-fx=none --foreground-color=black --exec="mc -b"

```
and it gives me the bottom result in the screenshot

just hitting alt+f2 and typing Eterm, then once inside eterm, toggling on transparency and black and white mode gives me the top results... wich is exactly what i want, minus the title bar and scrollbar

Any Eterm experts out there know what im doing worng or not including in the syntax thats causing the lines and other characters to be all wonky characters

---

### Post by Nythain on 2007-06-15
ok, so my problem aparenly lies in the --exec= portion of our tour... removing that and just running mc -b from the eterm manually displays it perfectly... any clues on how to properly use Eterms --exec argument/option

i have scoured the net and cant find any help with this... should i be using screen instead of exec??? i have absolutely not experience with screen and its options/arguments

---

