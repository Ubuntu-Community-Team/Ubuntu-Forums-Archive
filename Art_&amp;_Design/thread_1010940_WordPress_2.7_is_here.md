---
title: "WordPress 2.7 is here"
date: 2008-12-14
forum: Art &amp; Design
---

### Post by banago on 2008-12-14
Hi guys,

WordPress 2.7 is out and it is a great release. I suggest you use it as your blogging or CMS software.

Read more [here]("http://wordpress.org/development/2008/12/coltrane/") and [here]("http://www.wplancer.com/wordpress-27-one-small-step-for-a-the-team-one-giant-leap-for-the-users/")

---

### Post by Neon Lights on 2008-12-14
I looooooooove it! Love the new dashboard, and it's all just amazing. =] Wordpress is just awesome. <3

---

### Post by nolimit974 on 2008-12-14
I just upgraded to it and also installed a new theme too..tell me what you think...the link is in my sig.

---

### Post by -yay- on 2008-12-14
I hope they included the ability to turn off autosave this time, that stuff makes your database huge.


oh and banago, you got a typo in your article:
"official stabel version has been released"

"stable" not "stabel"

We wordpressers gotta stick together in the fight against typos ;)

---

### Post by banago on 2008-12-15
> **-yay- said:**
> I hope they included the ability to turn off autosave this time, that stuff makes your database huge.


oh and banago, you got a typo in your article:
"official stabel version has been released"

"stable" not "stabel"

We wordpressers gotta stick together in the fight against typos ;)

I love it that there are WordPress guys around here - I can even start a community as Ubuntu WordPress Lovers :)

Thanks for the typo - I would like to give you something back - here it is how to turn off auto-save in WP:

[http://lesterchan.net/wordpress/2008/07/17/how-to-turn-off-post-revision-in-wordpress-26/](http://lesterchan.net/wordpress/2008/07/17/how-to-turn-off-post-revision-in-wordpress-26/)

---

### Post by Greyed on 2008-12-15
I wish I WordPress' rich edit dialog didn't interfere with Firefox's own spell checker.  UF's rich edit doesn't have that problem.  I might not mind too much except it doesn't do on the fly spell checking nor is its checking all that great.  In a recent post it was telling me the word with was misspelled.  But only the th.  W[COLOR=Red]_TH_[/COLOR]?

Other than that Wordpress is very nice.  I do have some questions about it, though.  Maybe I'll ask those somewhere around here soon.  :D

---

### Post by banago on 2008-12-15
> **Greyed said:**
> I wish I WordPress' rich edit dialog didn't interfere with Firefox's own spell checker.  UF's rich edit doesn't have that problem.  I might not mind too much except it doesn't do on the fly spell checking nor is its checking all that great.  In a recent post it was telling me the word with was misspelled.  But only the th.  W[COLOR=Red]_TH_[/COLOR]?

Other than that Wordpress is very nice.  I do have some questions about it, though.  Maybe I'll ask those somewhere around here soon.  :D

Yes, the built-in spell checker is not very good.

As for the WordPress questions - you are at the right place - just write it down :)

---

### Post by -yay- on 2008-12-17
> **banago said:**
> 
Thanks for the typo - I would like to give you something back - here it is how to turn off auto-save in WP:

[http://lesterchan.net/wordpress/2008/07/17/how-to-turn-off-post-revision-in-wordpress-26/](http://lesterchan.net/wordpress/2008/07/17/how-to-turn-off-post-revision-in-wordpress-26/)

Already got that one :)
That's post revisions though, autosave is different, post revision saves a post everytime you make a change, autosave just saves every 60 seconds or so.

As far as I have understood autosave can't be turned off, only delayed by increasing the interval like this:

define('AUTOSAVE_INTERVAL', 60000);

It's a clumsy hack though, I wish they would just include the ability to turn it off.

---

### Post by banago on 2008-12-17
Aha, I see - I was misunderstood. I am sorry that you are in trouble, but why do you find it disturbing?

---

### Post by -yay- on 2008-12-17
> **banago said:**
> Aha, I see - I was misunderstood. I am sorry that you are in trouble, but why do you find it disturbing?

Don't worry, I'm not in trouble, I figured out how to turn off those things a long time ago :) I just think it's annoying that it's enabled by default in Wordpress.

The reason I don't like post revision and autosave is because they really make the MySQL database huge. The autosave creates one row inside the database for each post, making the wp_posts table twice the size it needs to be, and the post revision creates a new row every time you change your post. So if you change your posts often, you could end up with 5 rows per post, effectively making the MySQL database 5 times the size it needs to be. The larger the MySQL database becomes, the slower the website becomes.

---

### Post by Vincent Masamune on 2008-12-17
May I ask why would I need a CMS program? Can't I just edit my blog in my web browser?

---

### Post by Greyed on 2008-12-18
...  What do you think you're connecting to with your browser to edit your blog?

---

### Post by Vincent Masamune on 2008-12-18
> **Greyed said:**
> ...  What do you think you're connecting to with your browser to edit your blog?

I see. I wasn't quite lucid when I asked my question.

---

### Post by Funnnny on 2008-12-18
Used Wordpress for 3 year and still loving it :)

---

### Post by Izek on 2008-12-18
> **Vincent Masamune said:**
> May I ask why would I need a CMS program? Can't I just edit my blog in my web browser?

To edit that quote:

"May I ask why I would need to edit using a CMS Program when I could just make my own website with notepad? Or some other text editor?"

I don't really see a practical use for a CMS in the first place.

---

### Post by banago on 2008-12-18
> **Izek said:**
> To edit that quote:

"May I ask why I would need to edit using a CMS Program when I could just make my own website with notepad? Or some other text editor?"

I don't really see a practical use for a CMS in the first place.

First think you need to keep in mind is that a CMS (content management system) is different form a text/web editor. Also, the CMS is used to manage the content, not to create that (even though usually I use WordPress's text editor to write my articles. 

The CMS offers you the ability to store content in a database and allows you to categories the content into categories (and tags lately). Also, it allows you to query the content in different ways to front or other pages.

Another thing that the CMS offers is the ability to interact with the visitors through commenting systems and other abilities.

You can also have site archives and view content chronologically.

Also you can have more then ones users or an entire community managed by a CMS, WordPress in our case.

The bottom line, a CMS help you to write less code, automate updating processes and have more productivity.

I hope I was somewhat illuminating :)

---

### Post by Izek on 2008-12-18
Yes, it is more illuminating, but I still don't get what the fuss is about. I write a template and I just copy it if I want to make another page. In all, I need to write code basically once, and add more code (albeit, not very much more depending) when I make a page that requires more code.

I made a site completely with a text editor and the curvycorners script once to mimic the design of the Tales of the Abyss Menu. Granted, I lost that design. If wordpress can do this, I'd like to know how.

---

### Post by -yay- on 2008-12-18
I guess the biggest advantage of wordpress (or any CMS) is that people who do not know html, php and css can still create a dynamic web page with functions like threaded comments and spam control..

For people who already know how to code the biggest advantage is that they don't have to reinvent the wheel, they just create a theme if they want to customize.

Izek: you can create that in wordpress, but you would have to code your own theme though. Wordpress uses [template tags]("http://codex.wordpress.org/Template_Tags") to assist theme authors.

---

### Post by banago on 2008-12-18
> **Izek said:**
> I made a site completely with a text editor and the curvycorners script once to mimic the design of the Tales of the Abyss Menu. Granted, I lost that design. If wordpress can do this, I'd like to know how.

WordPress can handle any kind of design, drop-downs or anything. It just makes you have the code once and not repeated on every page.

---

### Post by jedimasterk on 2008-12-18
Big WHOOP!!. Where is Adobe Creative Suite!!. That would be BIG news!.

---

### Post by IKhider on 2008-12-19
Hello, 

Wordpress looks good. I installed it with Synaptic Package Manager, but do not see it on the toolbars anywhere. Any idea on how to get the thing fired up and running?

-I-

---

### Post by banago on 2008-12-20
I think you have just installed a GNOME plugin that allows you to post autamatically to a WordPress blog. To have WordPress installed locally you need XAMPP.

---

