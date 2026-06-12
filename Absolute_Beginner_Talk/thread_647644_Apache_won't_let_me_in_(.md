---
title: "Apache won't let me in :("
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2007-12-22
I installed apache on Kubuntu Gutsy

I'm not doing any heavy hosting, I just host some files that I share with some other people - it's an easy way to transfer files, FTP is a pain in the *** b/c most people don't have FTP clients.

Anyways, I went to the apache folder, which I thought was ~/var/www/apache2-default/

And I can't do ANYTHING.  All permissions are blocked...?  I can't save, I can't make a new file, I can't do jack ****.

Any ideas?

---

### Post by PriceChild on 2007-12-22
The actual root is /var/www, not /var/www/apache2-default/ or ~/var/www/apache2-default/

By default, it is owned by the www-data group, so you could add yourself to it to let you move things in. Alternatively, create folders inside it and chown them to yourself.

---

### Post by Syndacate on 2007-12-22
That doesn't make any sense.

When I type [http://localhost/](http://localhost/) I get a page up saying "It works!" - which is apache's default index.html page.

There's nothing except the "apache2-default" directory inside /www/ - the index.html file is in that direcotry (apache2-default) and if you edit it with kedit it's the one that has in there "It works!" - though none of the stuff in that directory is editable.

Anybody else?  Help?

On windows this would be the equivalent of "program files/apache software foundation/apache2.2/htdocs/" - where your "hosted folder" is...

---

### Post by PriceChild on 2007-12-22
Ah that's because of a funky setting in /etc/apache2/sites-enabled/000-default that looks a little like this:
```
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
```You just seem to have it uncommented.

---

### Post by Syndacate on 2007-12-22
Naw, I got what ur saying now, I threw a different index.html file in the main portion the main var/www/ directory and it works.

Thanks man.

---

### Post by Syndacate on 2007-12-22
Ah, I thought it was fixed but I was wrong.

The index.html page shows up fine in the /var/www/ thing, but if I try to type my IP/file name I get a 403 (access forbidden) error.

How the hell do I free up this directory so anybody can access it?

---

### Post by PriceChild on 2007-12-22
go to [http://localhost/](http://localhost/) and say if you see it.

---

### Post by Syndacate on 2007-12-22
Yeah, I do, I see it fine.

Though from a remote terminal - or even from my machine just typing in IP/FileName gives a 403

---

### Post by PriceChild on 2007-12-22
please paste the output of```
ls -l /var/www
```I guess you just have too restrictive permissions on the file.

Alternatively chmod it if you think you know what you're doing :)

---

### Post by Syndacate on 2007-12-22
> **Syndacate said:**
> Yeah, I do, I see it fine.

Though from a remote terminal - or even from my machine just typing in IP/FileName gives a 403

What do you mean "if I think I know what I'm doing?"

---

### Post by Syndacate on 2007-12-22
Yeah, it worked after I changed the permissions, I didn't realize that the persmissions on "all" were disabled.  I put the permissions of the file to "read" on "all" and it worked fine.

Of course I'm still experiencing the problem where whenever I go to download a file with firefox it crashes (instant quit).

You wouldn't happen to know the fix to that real quick by any chance would you?  Or a less resource intensive/just as versatile browser?  Or how to install flash? - LoL - Any of the above would work too ;)

---

### Post by PriceChild on 2007-12-22
Woohoo :)

And the "if you know what you're doing" bit meant "if you don't understand this, then just do what i said above" :)

Haven't a clue. Perhaps you could run "firefox" from a terminal and paste the messages when it crashes. I'd suggest a new thread :)

---

### Post by Syndacate on 2007-12-22
> **PriceChild said:**
> Woohoo :)

And the "if you know what you're doing" bit meant "if you don't understand this, then just do what i said above" :)

Haven't a clue. Perhaps you could run "firefox" from a terminal and paste the messages when it crashes. I'd suggest a new thread :)

Yeah, I did that, it's a bunch of widget errors.

I uninstaller all my widgets and it doesn't seem to be doing it anymore.

Not exactly what I wanted, but oh well.  Know any good lightweight (low resource) versatile browsers?

---

### Post by PriceChild on 2007-12-23
search for "internet browser" in synaptic and see what you find :)

---

### Post by Syndacate on 2007-12-23
Yeah, I know there's a lot in there, but I was looking for recommendations.

See, there's a lot of crap browsers there that are only good for viewing forums and such (and some not even that).

I'm talking stuff with flash/java interface (as some browsers seem to lack those, ie. konquerer doesn't seem to work right with A LOT of web-apps on sites.

---

