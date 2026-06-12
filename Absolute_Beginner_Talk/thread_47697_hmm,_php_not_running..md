---
title: "hmm, php not running."
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-09
I am only used to setting up PHP on a windows system so I am getting a bit confused on linux. PHP has installed fine but when I go to my php test page it is printing the source out (i.e php is not running)...is this a common problem?

---

### Post by DJ_Max on 2005-07-09
[QUOTE=gammyhand]I am only used to setting up PHP on a windows system so I am getting a bit confused on linux. PHP has installed fine but when I go to my php test page it is printing the source out (i.e php is not running)...is this a common problem?[/QUOTE]
 Did you install from source, or from binary? Is your webserver configured to execute .php files as PHP?

---

### Post by gammyhand on 2005-07-10
[QUOTE=DJ_Max]Did you install from source, or from binary? Is your webserver configured to execute .php files as PHP?[/QUOTE]
 I installed through synaptic (binary I guess). I presume you mean "is my web server parsing the php mime type as php?"? If so, yes it is.

Hmm...just looked in httpd.conf and all it contains is this:

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

Which is very weird!

---

### Post by gammyhand on 2005-07-15
[QUOTE=gammyhand]I installed through synaptic (binary I guess). I presume you mean "is my web server parsing the php mime type as php?"? If so, yes it is.

Hmm...just looked in httpd.conf and all it contains is this:

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

Which is very weird![/QUOTE]
 Anyone?

---

### Post by Kvark on 2005-07-15
Double check that you have the package libapache2-mod-php4

---

### Post by gammyhand on 2005-07-15
[QUOTE=Kvark]Double check that you have the package libapache2-mod-php4[/QUOTE]
 yes i do.

---

### Post by gammyhand on 2005-07-16
[QUOTE=gammyhand]yes i do.[/QUOTE]
 Any other tips?

---

