---
title: "Using the Find Command &amp; Apache2 Configuration"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by oxsyn on 2008-02-24
First, here's my goal: I installed apache2.  I know it's working cause i can http to the machine.  It's still got all the default settings.

In /etc/apache2/sites-available is the following:

> <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

Because of this, i assume that somewhere on my system, there is a /apache2-default/ directory that holds an index.htm or index.html file that is being displayed by my server. 

So, i'm trying to search for it, using the find command like: 

> find / /apache2-default/

... it finds nothing.  Similarly,

> find / apache*

finds nothing either.  So I assume that I'm using the command incorrectly.  And actually, I'd like to write the results to a file.  I tried:

> find / apache* > search.results

but the file ends up containing all the files & directories that DO NOT match apache*.

So, to recap: I want to use the find command to find the all directories and files on the server that match apache*, and I'd like the results written to a file search.results.  And to make sure, one of the lines in this file should reveal the path of the default apache2 directory, right?

THANKS!

---

### Post by oxsyn on 2008-02-24
Additional question: The default apache page contains the text "It works!" - is there a way to search all the files on the system for that text (in order to find the file I'm looking for?)

Thanks again!

---

### Post by oxsyn on 2008-02-24
Argh.  I always figure it out right after I post.  I was using the wrong find syntax, it should have been:

> find / -name "apache*"

it found the directory: /www/var/apache2-default/
which contains the index.html file that is displayed.

Now, I just have to figure out how to write the results of a search to a file.

---

