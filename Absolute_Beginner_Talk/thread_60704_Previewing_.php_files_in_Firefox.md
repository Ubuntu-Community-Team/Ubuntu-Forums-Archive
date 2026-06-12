---
title: "Previewing .php files in Firefox"
date: 2005-08-28
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-08-28
Okay, another dumb Mozilla on Linux question.
So, I work with a lot of .php files for my website, and in Windows, I can "open with" and pick my respective web browser to preview how it'll look. If I open a .php file with Firefox, it'll open in Firefox. If I open a .php file with Internet Explorer, it'll open with Internet Explorer.

For some reason, though, in Linux, when I try to open a .php file with Firefox, I get [this dialogue box](http://i22.photobucket.com/albums/b337/psychocats/9b1f41a4.png) that asks me what helper application (i.e., not Firefox itself) that I want to open it with. Needless to say, if I click "OK," nothing happens.

I'm assuming that in Windows, the associated helper application was somehow predefined, but I don't know what that helper application is. I already have php4 installed. 

Anyone know the workaround for this?

---

### Post by noob_Lance on 2005-08-28
try to install apache, installing php is useless without it =D.

cheers

---

### Post by aysiu on 2005-08-29
[QUOTE=noob_Lance]try to install apache, installing php is useless without it =D.

cheers[/QUOTE] Ok. Not sure if I'm doing this right, but I still get the dialogue. If I choose Apache as my helper application, the dialogue goes away (if I choose anything else, the dialogue reappears), but I get a blank page. What should I be doing?

---

### Post by Jussi Kukkonen on 2005-08-29
[QUOTE=aysiu]Ok. Not sure if I'm doing this right, but I still get the dialogue. If I choose Apache as my helper application, the dialogue goes away (if I choose anything else, the dialogue reappears), but I get a blank page. What should I be doing?[/QUOTE]
 You need to setup apache to serve those pages, and then open them not through a file path but through connecting to the apache web server... So instead of opening *file:///www-content/index.html* you open *[http://localhost/index.html](http://localhost/index.html)* (assuming /www-content is the directory apache is serving)

Apache has pretty good docs and tutorials, use them.

---

### Post by aysiu on 2005-08-29
[QUOTE=Jussi Kukkonen]You need to setup apache to serve those pages, and then open them not through a file path but through connecting to the apache web server... So instead of opening *file:///www-content/index.html* you open *[http://localhost/index.html](http://localhost/index.html)* (assuming /www-content is the directory apache is serving)

Apache has pretty good docs and tutorials, use them.[/QUOTE] Thanks. I'll investigate those.

---

### Post by gammyhand on 2005-08-29
[QUOTE=aysiu]Thanks. I'll investigate those.[/QUOTE]
 I don't know how you are getting windows to preview those pages in a web browser? Possibly ignoring the dynamic content. But PHP is impossible to parse without running through the web server (unless it's compiled).

---

### Post by aysiu on 2005-08-29
[QUOTE=gammyhand]I don't know how you are getting windows to preview those pages in a web browser? Possibly ignoring the dynamic content. But PHP is impossible to parse without running through the web server (unless it's compiled).[/QUOTE] No, you're right. It doesn't show the dynamic content, but it still gives me a basic look and feel of the static content, without includes or cascading style sheets.

---

