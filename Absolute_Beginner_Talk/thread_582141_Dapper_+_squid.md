---
title: "Dapper + squid"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by CVNChaotic on 2007-10-19
I am tasked with setting up a free hotspot, the easy part. I also need to add a footer to the bottom of all web sites viewed while on the hotspot. Sort of like "This hotspot brought to you by" type of thing. I I seem to remember squid being able to insert a footer, but I cant seem to figure it out...

any ideas? Is there a better way?

---

### Post by kidders on 2007-10-21
Hi there,

I know this really doesn't answer your question, but the "better way" is not to do it at all. Tbh, I would suggest giving serious consideration to finding other ways of plugging your company. You see, if asked to do so, I'm not sure your users would be able to come up with anything that could possibly be more infuriating than having every single web page they request mauled for no reason, particularly given that...[LIST]
[*]There is plenty of potential for data other than web pages to be affected, including downloaded archives, executable files, RSS feeds, and so on.
[*]Disabled users may find websites that would normally be accessible become partly (or completely) unusable, which may have legal implications for you, much the same as placing a sign that read "No wheelchairs allowed" outside your premises might.
[*]Javascripts may fail, CSS may be mis-applied, and so on, affecting layout & usability.
[/LIST]
For a proxy to alter the content of a web page is an express violation of the HTTP protocol specifications ... something you can't expect to be able to do without consequences. If the messages being appended read "There is a fire in the next building. Pleae evacuate immediately." you could be forgiven, but imagine not being able to open a Mac iDisk (or similar) because of an advertisement!

I've never seen a hotspot provider brasin enough to do the sort of thing you're describing, but something I *have* seen done is for users' first few requests to be redirected to advertisements & other messages (eg usage policies). Once they're out of the way, any applications that depend on accurate HTTP implementations can work unimpeded, but people are still made aware of who's providing the service they're using ... which is particularly important when it's free, imo.

---

