---
title: "Compiling the latest Edbrowse on Edgy"
date: 2006-11-24
forum: Assistive Technology &amp; Accessibility
---

### Post by benjaminhawkeslewis on 2006-11-24
Can anyone work out how to compile the latest version of Edbrowse (3.1.3), a customization of Ed to create a complete audio desktop complete with JavaScript-enabled web browser, on Ubuntu Edgy? I installed the SpiderMonkey  JavaScript library from source in /opt/edbrowse but I couldn't get Edbrowse itself to compile.

The Edbrowse homepage is at:

[http://www.eklhad.net/linux/app/](http://www.eklhad.net/linux/app/)

No matter what I do, I always get the same errors out of make:

jsdom.c:673: error: storage class specified for parameter ‘initScript’
jsdom.c:673: error: parameter ‘initScript’ is initialized
jsdom.c:717: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
jsdom.c:918: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
jsdom.c:925: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
jsdom.c:953: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
jsdom.c:970: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
jsdom.c:990: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
jsdom.c:1087: error: old-style parameter declarations in prototyped function definition
jsdom.c:19: error: parameter name omitted
jsdom.c:1087: error: expected ‘{’ at end of input
make: *** [jsdom.o] Error 1

---

### Post by kd7swh on 2006-12-06
I know you most likely want the 3.13 version but did you try the binary version  of 2.2.10.

did it run?

do you have a gcc log of the source you tried to compile?

---

### Post by benjaminhawkeslewis on 2006-12-11
I didn't try the version in the repositories. It wouldn't be very enlightening since in version 2 the developer was trying to create his own JavaScript implementation and in version 3 he gave up and started using SpiderMonkey, and the compilation problems appear to be related to that library. When you say a "gcc log" do you mean you'd like to see the entire output of make rather than the fragment from the end that I provided?

---

