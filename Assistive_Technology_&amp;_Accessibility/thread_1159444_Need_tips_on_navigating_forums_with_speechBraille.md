---
title: "Need tips on navigating forums with speech/Braille"
date: 2009-05-14
forum: Assistive Technology &amp; Accessibility
---

### Post by Deborah Norling on 2009-05-14
I would appreciate some tips on quickly navigating the Ubuntu web-based forums (like this one) using speech and/or 
Braille.

I've tried with Orca using Firefox; I've tried with JAWS using Firefox and IE in Windows, and I've even tried Lynx 
with speakup and brltty.

I'm an experienced user and administer a Hardy server running typical server apps as well as mythtv. I am 
constantly searching the forums for answers to questions.

With all screen access, I find that irrelevant information is repeatedly read, and the pages have no structure, 
like subheadings, to make navigation efficient. For example, I'm not interested in when each poster joined, how 
many beans and cups of ubuntu he had (whatever that means) whether he's online and how many posts he's made in the past. I don't want 
to read repeatedly through* each poster's other details, like his messaging contact screen names, or his location 
or the version of the software he's running.  I don't know what all this "a care for ubuntu" and "dark roasted 
ubuntu" stuff means either, but it appears in front of each post and slows down my search for information.

My sighted husband breezes thru these forums and in minutes, he *retrieves info it takes me hours to locate.

Can anyone explain what's going on, and why the ubuntu forums are such a nightmare to navigate with access 
technology?
Does anyone have solutions for getting through a large number of posts efficiently?
--Debee

---

### Post by Ubris on 2009-06-02
> **Deborah Norling said:**
> 
With all screen access, I find that irrelevant information is repeatedly read, and the pages have no structure, 
like subheadings, to make navigation efficient. For example, I'm not interested in when each poster joined, how 
many beans and cups of ubuntu he had (whatever that means) whether he's online and how many posts he's made in the past. I don't want 
to read repeatedly through* each poster's other details, like his messaging contact screen names, or his location 
or the version of the software he's running.  I don't know what all this "a care for ubuntu" and "dark roasted 
ubuntu" stuff means either, but it appears in front of each post and slows down my search for information.

You're certainly right about the lack of structure in the page markup and the verbose description of each forum poster which offers no means of skipping over. All that useless information is given equal importance in the markup to the message itself. The post titles are just marked up strong, not headings. I tried some forum pages in lynx to get a sense of exactly how bad it is.

In short, the forum software being used is structurally and semantically very poor. They haven't thought of anything but sighted users competent with a mouse. I think you have guessed all that. The software seems to be something called [vBulletin]("http://www.vbulletin.com/"). It seems to be closed source software. I can't see a way around your issues with this tool.

I think your best chance is to escalate your complaint and have the software changed to something a lot more accessible. It makes me angry that a community like this would choose such an exclusionary tool, but I'd also like to hope it is only through ignorance that it was selected. You have a right, as does every web user with standards-based tools, to a fully featured and equal experience.

I'm going to think about what I might be able to do to draw attention to this problem.

---

### Post by Sef on 2009-06-02
Another mod, dmizer, has a couple of suggestions:

1)  User CP > Edit options > Thread Display Options and uncheck all three.  

2) Thread Tools > Show Printable Version, but that does not allow replies.

---

### Post by Sef on 2009-06-02
Ubuntu Geek has this link:  [http://ubuntuforums.org/archive/](http://ubuntuforums.org/archive/).  You cannot reply.  He said "while not ideal its the best we can do right now."

---

### Post by srippon on 2009-06-07
Dear Deborah

Am really sorry to hear you're having trouble accessing the Ubuntu Forums.  I am a User Experience practitioner with skills in web accessibility and have been wondering about the accessibility of this forum.

I've logged an idea in the Ubuntu Brainstorm site to [improve accessibility of Ubuntu Forums]("http://brainstorm.ubuntu.com/idea/20164/").  When I get a chance I'll start looking into performing a [WCAG2.0]("http://www.w3.org/WAI/intro/wcag.php") evaluation of some of the Ubuntu Forum pages.

Kind regards,
Scott Rippon.

---

### Post by srippon on 2009-06-07
Dam didn't realize the forum software was proprietary! :(
I know this is off-topic but why are the Ubuntu Forums powered by closed source proprietary software?

Scott Rippon.


Mod Note: [Answer]("http://ubuntuforums.org/showthread.php?t=1768&highlight=phpbb") to your question.  See post 4.

---

### Post by OscarFoxtrot on 2009-06-24
> **srippon said:**
> I've logged an idea in the Ubuntu Brainstorm site to [improve accessibility of Ubuntu Forums]("http://brainstorm.ubuntu.com/idea/20164/"). 

Umm, that site's got a vision-only CAPTCHA on it to sign up.

---

### Post by Henrike Corinna on 2009-06-30
1)  User CP > Edit options > Thread Display Options and uncheck all three.  

2) Thread Tools > Show Printable Version, but that does not allow replies.                                                                                               __________________
Learning is not attained by chance, it must be sought for with ardor and attended to with diligence. Abigail Adams ( 1744 - 1818 ), 1780;

---

### Post by Deborah Armstrong on 2009-10-07
[PHP][/PHP]I am the original poster of this thread, but am now using an account with my married name.  One day I have to figure out how to link my old account to this new account.
Anyway, I figured out a few interesting things. Posting seems even less accessible, but I think most of those problems are caused by  screen access reading the wrong captions.  For example, the edit box, where you actually type the message is captioned "wrap PHP tags around selected text" which is an artifact of the clickable elements which let you HTML-ize your post. Also it appears first in the tab order as soon as you enter a title, that is, after you complete entering your title, the entire tab order of the page changes dynamically, with the edit box for entering the message appearing first.

The designers of this forum should really try using it without a mouse for a couple of days!

There is a caption labeled "message:" but it's not attached to any form field.
 
When reading posts, I wonder if there's a way to set things up so that the relevant information is in a specific color. Most screen access can read, say just what's in red and skip the rest.
As the other poster said, I think the biggest usability enhancement would simply be to add structure elements, like headings and to make sure that tab order on form fields was fixed -- Oh and to make sure that form fields didn't dynamically appear and disappear, either.
Some of these form fields don't "appear" to screen access until you actually enter a title.

---

