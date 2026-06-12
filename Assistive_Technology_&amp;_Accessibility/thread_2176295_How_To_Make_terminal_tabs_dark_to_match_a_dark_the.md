---
title: "How To: Make terminal tabs dark to match a dark theme"
date: 2013-09-23
forum: Assistive Technology &amp; Accessibility
---

### Post by Colin_Deisenroth on 2013-09-23
If you are using a dark color theme in terminal you would have noticed that ever since 11.04, the terminal tabs don't match the theme of the terminal themselves.

Here is an example of what the tabs would have looked like in 11.04
[IMG]http://i.stack.imgur.com/JHc5s.png[/IMG].

Since then, tabs will be white even in a dark theme.

If you want to get dark tabs back, I haven't figured out how to make them look exactly the same, but here is a dark theme that is at least similar and looks much better than the white tabs.

Create/modify a file in the following location
~/.config/gtk-3.0/gtk.css

```
@define-color light-grey #3c3b37;
@define-color dark-grey #292929;
@define-color burnt-yellow #645c3e;
@define-color black #000000;


TerminalWindow .notebook {
/*    border: 0; /* set to any # to remove border around the active tab */
    border-width: 0; /* extra border around the terminal body with gray color */
    padding: 1; /* thickness of border width around terminal body, including under tab */
    background-color: shade(@burnt-yellow,1); /* color of padding around terminal body */
    color: #ffffff; /* color of text on tabs */
}


TerminalWindow .notebook tab:active {
    background-color: shade(@burnt-yellow,1); /* color of active tab */
}


TerminalWindow .notebook tab {
    background-color: shade(@dark-grey,1); /* color of inactive tab */
}

```

Close all terminal windows and re-open to have the new tab themes go into effect. This is basically just css as you can tell, so you are free to modify colors and borders to your liking.

Hope this helps someone else who is sick of looking at white tabs in a black terminal (and a plea to bring back the black tabs from 11.04).

-Colin

---

### Post by vasa1 on 2013-09-24
> **Colin_Deisenroth said:**
> ...
```
@define-color light-grey #3c3b37;
@define-color dark-grey #292929;
@define-color burnt-yellow #645c3e;
@define-color black #000000;
...

```
...
Your use of `light-grey`, `dark-grey`, etc is new to me. I thought we were restricted to things like `bg_color`, 
`fg_color`, `base_color`, etc.
Thanks for posting :)

---

### Post by 2td0m-andreas on 2014-09-19
A small detail: some white colored pixels still shine through the rounded corners of the tabs. I was able to eliminate these by making tabs entirely square, by adding "border-radius: 0" to the first block.

---

