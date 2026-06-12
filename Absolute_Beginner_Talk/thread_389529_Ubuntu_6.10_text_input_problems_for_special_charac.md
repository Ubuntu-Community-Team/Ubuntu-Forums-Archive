---
title: "Ubuntu 6.10 text input problems for special characters"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by plushpuffin on 2007-03-20
Hello,

I am just starting to use Linux as a programming tool for CS classes, and there is some very annoying functionality that I have been unable to identify.

Whenever I hit the double-quote or apostrophe or tilde key, the character does not immediately appear, but waits for me to type another character.

For example, if I hit single-quote  and then s, I will get the character &#347;. If I hit tilde and then u, I will get the character &#361;. Given that I am trying to program, the extra work I have to go through to type single and double quotes is really, really annoying.

This happens in ALL applications and text boxes, including terminal windows. I thought it might have been SCIM, but I removed it using Synaptix and the problem did not go away, even after logging in and out (I was just flailing in the dark with SCIM, I really don't even know what it does).

I tried web searching for this, but the problem is so hard to describe that I didn't have any luck. Could someone please tell me how I can turn this off? I don't want to type accented characters, I don't care about that. I just want my keyboard to function normally.

I'm sorry, I just realized that "accessibility" doesn't include foreign language characters. If I don't get a response here, I'll post in a more general forum, but I thought that an input-method-related problem would be appropriate in this forum.

---

### Post by frafu on 2007-03-21
The keys that don't type anything and that alters the character that you type next, are called *dead keys" (if I remember correctly). 

I don't know what is the official handling of dead keys in Ubuntu, but they are useful to type letters with diacritical marks (accents,...) that are present in many languages. 

I don't know whether there is a simple way to turn off dead keys. 

Have you tried using the standard US keyboard layout? If you set the keyboard preferences to the US layout, your keyboard will behave as a US keyboard. The drawback will be (I am assuming that you do not have a US keyboard) that the labels on the keys will not correspond to what is being typed, but it might be more convenient when writing programs, once you know by heart which key types which letter. 

May be somebody with more knowledge than me will post a reply that will help you better. 

I am going to move your thread to the "Absolute Beginner Talk" forum, where it will be more appropriate and where you might get more answers. 

Have a nice day. 

Francesco

---

### Post by plushpuffin on 2007-03-21
Thank you frafu, all I really needed was the phrase "dead keys" and I was able to search and figure it out for myself. I didn't realize that the keyboard layout categories themselves were selectable, and I had selected "US English (intl)". After selecting just plain "US English" my keyboard is now working normally.

---

### Post by Billy Bong on 2007-03-22
Thank you Plushpuffin!

I didn't realise that you could select "US English" as an option. I just assumed it was a heading and not selectable...clicked on the triangle and selected from the sub-menus.

Cheers

Billy

---

### Post by saulysw on 2007-04-24
All,

I also fell into this trap. During installation (in this case, 7.04) I had to choose the keyboard layout, as we all did. The keyboard layout for "U.S. English" looks like a sub-menu heading, and it wasn't initially obvious that it was actually selectable. I expanded it out, and chose the thing that looked the closest to the one I wanted, which was "International (with Dead Keys)". I perhaps gave this 5 seconds of thought, checking that the other sub-menu items were not the ones I wanted.

This seemed fine until I had need to type a quote, double quote, tilde and anything else slightly off beat. Curiously I got it to work with two key presses, but I knew it was an issue with the layout. It took me a minute to realize my mistake, and although I am a Ubuntu newbie, I have been using computers for decades and if I can make this mistake I'm sure others will too. This issue, and the problem of not being able to get my LCD monitor at the right resolution (bound to 800x600) gave a not-so-positive impression of the operating system. The problem is fixed easily enough by going to the System : Preferences : Keyboard menu and changing it to the right layout.

My suggestion, for what it's worth, is to have the "U.S. English" or perhaps "Standard Layout" listed in the sub-menu. Yes, I know that would mean it's repeated with the section heading, but it mean a lot less likely that someone will choose the wrong layout. Those in the know of being able to select the section heading will be not disadvantaged. Makes sense to me anyway.

- Saul

---

