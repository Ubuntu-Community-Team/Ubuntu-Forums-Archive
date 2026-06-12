---
title: "Right Alt key = left Alt key?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by zmike1 on 2007-07-07
I have learned a lot about ¨why¨ the right Alt key is configured to be different from the left Alt key and how to compose special characters but what eludes me is:
How do I make my right Alt key do the same thing as my left Alt key?

per the forums, I´ve tried modifying xorg.conf as below:


{Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"alt-intl"
	Option 		"XkbOptions" "compose:rwin"
EndSection}


Alternatively, if I could make the right Win key behave like the left Alt key, it would do...

BTW, I´m using Feisty, Xubuntu; therefore, going to Settings->keyboard settings--> layouts does not give me any option for ¨level 3 characters¨

---

