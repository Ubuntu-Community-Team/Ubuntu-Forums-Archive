---
title: "[B]how to config PostgreSQL in Ubuntu[/B]"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by itisgood on 2006-09-26
hi everyone,
im new to ubuntu, actually just finished dual boot installation last night.


i installed my postgresql trough <Add/Remove Applications>

the packages i have installed are 

< postgresql-8.1 >
< postgresql-client-8.1 >
< postgresql-client-common >
< postgresql-common >

but after it finished installation, i coulndn't log in to the database,

jyao@jyao-laptop:/$ psql
psql: FATAL: database "jyao" does not exist
jyao@jyao-laptop:/$ psql postgres
psql: FATAL: role "jyao" does not exist
jyao@jyao-laptop:/$ psql postgres -u
psql: Warning: The -u option is deprecated. Use -U.
User name: postgres
Password for user :
psql: FATAL: Ident authentication failed for user "postgres"
jyao@jyao-laptop:/$ psql postgres -u
psql: Warning: The -u option is deprecated. Use -U.
User name: jyao
Password for user :<i typed pwd>
psql: FATAL: role "jyao" does not exist
jyao@jyao-laptop:/$

jyao is the user of the ubuntu

is there any place that i should config?
and i also dont know how to start the actual server.
because there is no such command as <start>.

can anyone help me plz.....

thx a lot

---

### Post by Metacarpal on 2006-09-26
Hi, and welcome to Ubuntu!

Before I point you in the right direction for configuring postgreSQL, let me help you out with forum posting. :) First, I just wanted to say that you used a great title for your post.  However, don't try to use bold tags for your title, for two reasons:
1) any post that an individual hasn't read yet (or one they have read but there are new posts) shows up as bold, so the tag won't work; and
2) trying to make your post appear more important than others could turn potential helpers off from reading it.  It's just a forum faux-pas - don't worry, a lot of us do that sort of thing at first.

Also, try to limit yourself to [one post per problem]("http://www.ubuntuforums.org/showthread.php?t=265886").  Double-posts can also turn away some would-be helpers.  If you don't get an answer right away, it's probably just because no one familiar with your issue has checked the boards yet.  There are a lot of us (myself included) who go hunting for zero-reply threads to help on.  We'll find you sooner or later.

So, that said - [here's a great resource]("http://www.postgresql.org/docs/8.1/interactive/index.html") for all your postgreSQL needs, in convenient html format with links.  If you're already familiar with the syntax of postgreSQL commands (they're a little different here and there from, say, Oracle), then you might want to skip straight to the [server administration page]("http://www.postgresql.org/docs/8.1/interactive/admin.html").

---

