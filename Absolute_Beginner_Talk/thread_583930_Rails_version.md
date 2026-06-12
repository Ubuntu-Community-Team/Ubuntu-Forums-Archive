---
title: "Rails version"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by rgreen on 2007-10-20
I have installed ruby, rails and rubygems via apt-get. Every time I run "rails -v" I get the folllowing error:getopt: invalid option -- v
Help!!

---

### Post by llamakc on 2007-10-20
ken@llamakc 04:45:07:~$ apt-cache show rails
Package: rails
Priority: optional
Section: universe/web
Installed-Size: 16132
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Adam Majer <adamm@zombino.com>
Architecture: all
**Version: 1.2.4-1ubuntu1**
Depends: ruby, ruby1.8 (>= 1.8.2-3), rake (>> 0.7.0), rdoc (>> 1.8.2), libsqlite3-ruby1.8 | libpgsql-ruby1.8 | libmysql-ruby1.8 | libdbi-ruby1.8, libredcloth-ruby1.8, liberb-ruby
Recommends: irb (>> 1.8)
Suggests: libapache2-mod-ruby | libapache-mod-ruby | libapache2-mod-fcgid, libfcgi-ruby1.8
Conflicts: libdevel-logger-ruby1.8
Filename: pool/universe/r/rails/rails_1.2.4-1ubuntu1_all.deb
Size: 2283536
MD5sum: 84532ec5a09ebec90252991601883c02
SHA1: 4fef08f3c63f92a1822f47f7128aa5c4c01179c0
SHA256: 5e49e3e82fba3c9824164686d9552e92878269f0de51afd752d5c4bbb7b67c84
Description: MVC ruby based framework geared for web application development
 Rails is a full-stack, open-source web framework in Ruby for writing
 real-world applications.
 .
 Being a full-stack framework means that all layers are built to work
 seamlessly together. That way you don't repeat yourself and you can
 use a single language from top to bottom. Everything from templates to
 control flow to business logic is written in Ruby.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by rgreen on 2007-10-20
I don't understand.

---

### Post by llamakc on 2007-10-20
When you typed "rails -v" were you trying to get the version of rails, or something else?

Documentation for rails is at /usr/share/doc/rails also.

---

### Post by rgreen on 2007-10-20
Version of rails.

---

### Post by Frak on 2007-10-20
> **rgreen said:**
> Version of rails.
Version: 1.2.4

---

### Post by rgreen on 2007-10-20
Actually it's 1.2.5.

---

### Post by llamakc on 2007-10-20
> **rgreen said:**
> Actually it's 1.2.5.

How did you surmise that?

---

### Post by rgreen on 2007-10-21
When the installation finished it showed me the version number.

---

### Post by llamakc on 2007-10-21
How did you install it?

---

### Post by 2muchtea on 2008-03-17
You have to add the path of the installed gem in the PATH. I had the same problem and I did this : 
PATH=/var/lib/gems/1.8/bin:#{PATH} 
Note: I had Ruby 1.8.6

---

