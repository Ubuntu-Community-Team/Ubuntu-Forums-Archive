---
title: "Apache2 issue..."
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by JasonNewb on 2006-06-22
I recently installed Apache2 and I created a new folder in the /var/www folder.   Well, none of the files in that folder show up in the browser.  I dont get an error though.  Do I have to add it into the sites-enabled list somehow?

thanks!

---

### Post by verbatim210 on 2006-06-23
editting the contents of /var/www folder is effective immediately.  so you can try to this...

1. make sure ur apache is functional
     sudo /etc/init.d/apache2 restart

2. open web browser and look up "localhost"

if your browser loads, u should see the contents.  let us know how it goes.

---

### Post by JasonNewb on 2006-06-23
The www folder works fine and so does the apache2-default folder.  The only folder that doesnt work is the new one I made.  The permissions are all the same as the others.  Group and other have read permissions.

---

### Post by JasonNewb on 2006-06-23
Just a bump...

---

### Post by oscar on 2006-06-23
What is in the folder? Have you tried accessing
[http://localhost/folder/file.txt](http://localhost/folder/file.txt) (or whatever your files in there are)
I didn't have to do anything to get other dirs working.

---

### Post by JasonNewb on 2006-06-23
Hmm, I just put some HTML files that I had from an old site in there.  One has a Java applet that runs, but thats all.  I tried just a plain HTML file too.  The wierd thing is I get no errors.  Just a blank white page.

I just loaded the white page and looked at it, the HTML code is there when I view source.  Is it something with the java applet then?

---

### Post by alanphil on 2006-06-23
I would start with a very simple "HELLO WORLD" HTML page. No java applet, nothing fancy. Verify that this simple page works as expected.

If that's OK, then the next step would be to start looking at browser plugins that you might need for a java applet, etc.

---

### Post by verbatim210 on 2006-06-25
from what i've read it seems like your apache is working its just displaying a website which hides the contents.

might be a good idea to show us your site, what is the link?  visual references prove wonders in the world of troubleshooting :)

1 picture a thousand words etc etc.

---

