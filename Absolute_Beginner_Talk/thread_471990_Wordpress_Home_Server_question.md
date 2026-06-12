---
title: "Wordpress Home Server question"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-06-12
I set up a home server using LAMP and everything is great, except if I am on a different computer I can't see the wordpress html and colors and such, just 
[IMG]http://i10.tinypic.com/5y1qhyr.png[/IMG]

How can I fix this?

---

### Post by lazyart on 2007-06-12
Can't see.  Link to your site?

---

### Post by tdrusk on 2007-06-12
> **lazyart said:**
> Can't see.  Link to your site?

[http://techaspect.podzone.net/wordpress/](http://techaspect.podzone.net/wordpress/)

when on the server computer everything shows up like it's supposed to.

---

### Post by az on 2007-06-12
In the wordpress configurations, it probably thinks it's called "localhost" instread of your url.

See here:

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by lazyart on 2007-06-12
I viewed the source of the page and you have numerous references to localhost. For example:```
	<style type="text/css" media="screen">
		@import url( http://localhost/wordpress/wp-content/themes/classic/style.css );
	</style>
```
I don't have the syle sheet on my machine so I cant see the formatting.  You have it on your localhost, so it works for you.  Those should be relative references, not absolute.

Remove "http://localhost/wordpress" from that line and replace it with "." and see if it looks better for everyone.

Listen to the above poster's instructions.  Mine are probably too deep for Wordpress setup.

---

### Post by tdrusk on 2007-06-12
> **az said:**
> In the wordpress configurations, it probably thinks it's called "localhost" instread of your url.

See here:

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

:) 

It aggravates me that I didn't notice that. Thank you.

---

### Post by lazyart on 2007-06-12
I see you made the change.  Much better!!

---

### Post by tdrusk on 2007-06-12
I mite as well ask this here so I won't be cluttering the boards.
I went to upload my xml file with previous posts into wordpress  and got 
> Unable to create directory /var/www/wordpress/wp-content/uploads/2007/06. Is its parent directory writable by the server?
I know it's because the folder is only accessed by root. Is there any way to get around this besides getting on the server and doing it?

---

### Post by lazyart on 2007-06-12
Maybe this will be of help: [http://codex.wordpress.org/Changing_File_Permissions](http://codex.wordpress.org/Changing_File_Permissions)

Specifically> You can make all the files in your wp-content directory writable in two steps: 

Go to your WordPress main directory, with a command like cd wordpress/ 
Enter chmod -R 777 wp-content 

---

