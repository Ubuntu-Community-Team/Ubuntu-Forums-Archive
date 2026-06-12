---
title: "Character codes dosn't display correctly in client browser"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-04-15
Hey all
When I'm making new php files and writing them in Gedit, norwegian characters such as æ, ø and å won't display properly in client browser or sourcecode. This happens both from a remote host (unix) and localhost.
If i edit existing scripts orginally written in notepad++ (or just notepad) on a windows machine, it's all cool.
Example may be to add another newsitem or to hardcode norwegian characters in a current php file.

I've been doing some research and if I transport a php script made on my Linux desktop over to my Windows one, I get weird characters instead of 'new line's in the code. I'm guessing that this has something to do with each of the platform using different character code for that kind of input? (\r\n)

Anyway, fixing the characters in the sourcecode in windows that orginally was written in Linux dosn't seem to help much as the client browser still won't display the characters correctly.

If I make a new php file with the same content, then uploads it to the webserver and refreshes client browser, the characters are displayed as they should.
Is Gedit using some sort of meta data to decide how characters should look or be displayed that follows the php file? I've been searching the User Preference and other options without any mentioning of this...

Any ideas?

---

### Post by souki on 2006-04-15
you have to use the same character encoding between apache server and your text editor
if you want utf-8 encoding :
apache directive :
```
AddDefaultCharset UTF-8
```
your text editor follows the default charset encoding defined in your environnement (replace en_US with your locale):
```
LANG=en_US@UTF-8
```

you might also check the html header :
```
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
```

---

### Post by Nunyah on 2006-04-16
Thanks, typing locale in cmd told me I was using the norwegian version of UTF-8 . Apache seems to handle both from what phpinfo() could tell. As long as I use UTF-8 instead of ISO-8859-1 in the header of my document, it is displayed correctly.

I'm a bit concerned about portability, though. Since newline's and other characters aren't displayed as they should if I transfer the code over to windows and edit them, this might be a problem if I one day decide to to so.. I don't wanna get chained down to one OS. Moving a sourcefile from windows to linux works great, just not the other way around.

---

