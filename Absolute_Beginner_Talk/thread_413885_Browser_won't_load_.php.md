---
title: "Browser won't load .php"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by scaredinjuly on 2007-04-19
I'm running Dapper for a server

I'm having a problem viewing .php files I put into my public_html

Every time I try to load the paper, it asks if I want to save the files or open them, it won't let me view them on the browser page.

I probably screwed something up or didn't install something.

Any suggestions?

---

### Post by LaRoza on 2007-04-19
The server either doesn't know it has to interpret the .php files (configure it)

****************OR***************

Php is not installed (download it)

If you are using apache, php should already be there.

Make sure the file extension is what the server expects, if it requires .php use it, if it wants php5 use that.

---

### Post by scaredinjuly on 2007-04-21
I'ts working (kind of) now.

As it turns out, php5 didn't install with apache or MySQL

Thanks a bunch!

But now I have a new problem...
I can open .php files in my browser now, but they show up blank.

I was told I need to load the .sql file???
The server's for school, so I'm not supposed to install extra programs.
Is there a way to do this through the terminal?

---

