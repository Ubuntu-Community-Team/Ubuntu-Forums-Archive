---
title: "Xubuntu and polytonic (ancient) greek: how?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by tico on 2007-08-06
Hi,

does anybody can type polytonic (ancient) Greek using pure Xubuntu? I have installed the Greek Polytonic keyboard, but I can only use the acute accent (as in modern Greek): no other accents nor breathenings.

Any idea about how to solve this problem?

Thanks.

---

### Post by kostkon on 2007-08-06
Before anything else, I would like to ask you if you use a font that has support for Greek polytonic characters.

---

### Post by tico on 2007-08-06
> **kostkon said:**
> Before anything else, I would like to ask you if you use a font that has support for Greek polytonic characters.

Yes, I'm using a unicode font for polytonic Greek (Palatino Linotype). I could type polytonic Greek in Ubuntu Feisty, but I cannot do it in Xubuntu.

---

### Post by simosx on 2007-08-08
What is your system locale when you run Xubuntu?

---

### Post by Al3xK3aton on 2007-08-08
Why do you have two threads asking the same question? I already told you in the other thread to just use PICTURES of polytonic greek.

---

### Post by tico on 2007-08-09
> **Al3xK3aton said:**
> Why do you have two threads asking the same question? I already told you in the other thread to just use PICTURES of polytonic greek.

Sorry for having made 2 posts, but one was about Xubuntu and the other about Ubuntu. The solution may be (I don't know) different.

Concerning PICTURES, this will never be a solution to type polytonic Greek. Believe me.

Thanks.

---

### Post by simosx on 2007-08-10
What we miss here is to know whether it works/it doesn't work.

It's important to give this feedback.

---

### Post by tico on 2007-08-10
simosx,

I've answered in the other post (about Ubuntu). But here's is my answer (maybe someone will not find this other thread):


Thanks for your help. I've read your blog and tried two of your tips. Here are the results:

Tip one: You can edit /usr/share/X11/locale/compose.dir so that for your locale, the compose file is the Greek one, /usr/share/X11/locale/el_GR.UTF-8/Compose.

RESULT: polytonic Greek works fine, but accents for other languages that use the Latin alphabet (characters like á, é, ê, ã, õ etc.) don't work.

Tip two: You can edit the Greek compose file, take the Greek Polytonic section and update the Greek Polytonic section of en_US.UTF-8/Compose.

Worked perfectly.

[COLOR="Red"]**BUT there's another solution a little bit easier, I think**[/COLOR]. This solution was kindly given to me by Jan Willem Stumpel ([http://www.jw-stumpel.nl/](http://www.jw-stumpel.nl/)) and is similar (but easier) to the second tip. Here's his answer/solution:

I cleared all the problems with the breathing signs by becoming root and
editing the /usr/share/X11/locale/en_US.UTF-8/Compose file. I
replaced everywhere

   U10000313 by U0313
   U10000314 by U0314

and restarted X. [end of quotation]

This works fine. Just replace U10000313 by U0313 and U10000314 by U0314 in the Compose file and it will work.

What do you think of this way, simosx? Let me know.

Thanks once more for you help.

---

