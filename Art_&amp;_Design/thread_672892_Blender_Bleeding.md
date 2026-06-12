---
title: "Blender Bleeding"
date: 2008-01-20
forum: Art &amp; Design
---

### Post by RemmyLee on 2008-01-20
Okay. I feel that I have completed enough of the work to go ahead and post this here.

[[IMG]http://farm3.static.flickr.com/2381/2205271577_0a43d76a8b.jpg[/IMG]]("http://farm3.static.flickr.com/2381/2205271577_1bb6f93da8_o.png")

Blender Bleeding is a website that contains the bleeding edge version of Blender from the subversion source that is updated twice daily with 32 and 64 bit builds for Linux, released as Debian packages.

To achieve this, I created extensions to the default scons scripts system that Blender uses for building. With my additions, Blender now creates the Debian packages if **scons debian** is passed at the command line.

The automation is handled via cron and a shell script and the picture above is the proposed website desgin. As you can see, I based it on the official Blender website.

I'd like to thank the people over at the blenderartists forums for inadvertently being my beta testers for the builds.

It's not 100% yet. I need to rewrite on php scripts for the site to point to the new sub-domain and then go through everything with a fine tooth comb to make sure it's working perfectly.

Any C&C on the site would be very much welcomed.

---

### Post by RemmyLee on 2008-01-20
I think that I have everything worked out here.

[Here is the site]("http://blender.detroitguy.com/") if anyone is interested. I may eventually add apt links.

For some reason, the Ubuntu repositories still contain Blender 2.44, while 2.45 has been out for quite a long time.

---

### Post by King_Critter on 2008-01-21
Overall, I'd say it's a pretty nice site design. Nice idea, too. :P

There's just to things regarding the design -- first, the page title is currently "blender bleeding." However, I think it would look better if you capitalized the b's -- e.g. "Blender Bleeding." Second thing is that the pop-up window for downloading the packages is... meh. I think a separate HTML page would look more professional. 

But anyways, those are my thoughts. Like I said, it's a good idea, so I hope you keep it going. Good luck. :)

---

### Post by RemmyLee on 2008-01-21
Thanks for the input. I've already started making changes based on it. The download window now opens in the current page and I'm about to do the same with the change log.

---

