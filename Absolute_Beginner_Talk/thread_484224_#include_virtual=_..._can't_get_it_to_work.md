---
title: "#include virtual= ... can't get it to work"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Jombee227 on 2007-06-25
Hey all!  I hope this is the right spot for it, but I can't get the following line to work:

<!--#include virtual="/_includes/footer.inc" -->

In the source it just spits out exactly as above: <!--#include virtual="/_includes/footer.inc" -->

in the httpd.conf file i have:

AddType text/x-server-parsed-html .html .htm .shtml .inc

any ideas?

---

### Post by DBStevens on 2007-06-25
Changes are required in three places:

in 000-default

You need to add Includes to the html directory option line

then you need to place a copy of 

include.load form the mods_availible into mods_enabled

then in apache2.conf you need to have 

    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml

in the 

<IfModule mod_mime.c>

</IfModule>

block.

Then restart the server.

---

