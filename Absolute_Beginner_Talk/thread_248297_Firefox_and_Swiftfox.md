---
title: "Firefox and Swiftfox"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Surf Man on 2006-08-31
Does anyone know how to diassociate Firefox from gnome-app-install and yelp packages. I couldn't remove firefox without also removing those packages. And I also found that Swiftfox didn't show up on my applications menu after I installed it. It did show up on Synaptic package manager as being installed, but not on menus for application. Is there a special folder I need to install it in??? Why can't I completely uninstall Firefox without taking out the gnome-app-install and yelp? :cool:

---

### Post by Surf Man on 2006-08-31
Something doesn't feel right with the Firefox. It feels like it bogging down somehow. Swiftfox is supposed to streamline some of the issues with linux. Any advice on what settings when you enter about:config in the address bars that might fix or speed up the firefox. I am running with a router and high speed cable connection and the other machine, running you know what is faster.

---

### Post by Kilz on 2006-08-31
> **Surf Man said:**
> Something doesn't feel right with the Firefox. It feels like it bogging down somehow. Swiftfox is supposed to streamline some of the issues with linux. Any advice on what settings when you enter about:config in the address bars that might fix or speed up the firefox. I am running with a router and high speed cable connection and the other machine, running you know what is faster.

The only thins Swiftfox speeds up is the startup. Once its up the pages load about the same. Swiftfox is also NON Free software. It is not distributed under the MPL or GPL and cant be redistributed. So I dont recommend anyone using it. Its kind of like the Tivo of browsers.

---

### Post by Surf Man on 2006-09-01
[http://www.getswiftfox.com/releases.htm](http://www.getswiftfox.com/releases.htm)

I don't see where they are charging and it is supposed to be streamlined for each cpu type. I am wondering if some of the configs mentioned in link there are good to use in the setup for Firefox the setting that you can toggle when you enter about:config in the address bar. Anyone got any tips for speeding up Firefox?

---

### Post by catlett on 2006-09-01
[http://doc.gwos.org/index.php/DapperGuide#How_to_load_Web_site_faster_in_Mozilla_Firefox](http://doc.gwos.org/index.php/DapperGuide#How_to_load_Web_site_faster_in_Mozilla_Firefox)

---

### Post by Surf Man on 2006-09-01
Right on. I typed in "about:config" in firefox address bar and changed setting to those suggested on the link. Lots of reading to do there. Thank you kindly. Lots of variables there. Seems like firefox is a bundled tightly with ubuntu and was wondering why it takes gnome-app-install and yelp with it if you uninstall?

network.dns.disableIPv6 -> true 
network.http.pipelining -> true 
network.http.pipelining.maxrequests -> 8 
network.http.proxy.pipelining -> true

For the no menu item for swiftfox after installed someone else had a similar problem and started the application from terminal and then make shortcut to desktop. May be idea to get swiftfox installed if I go that way. See if this helps.

---

### Post by justin whitaker on 2006-09-01
> **Kilz said:**
> The only thins Swiftfox speeds up is the startup. Once its up the pages load about the same. Swiftfox is also NON Free software. It is not distributed under the MPL or GPL and cant be redistributed. So I dont recommend anyone using it. Its kind of like the Tivo of browsers.

There are no charges listed on their website, and the blogs and forums are mute on the subject. I don't really see an issue with the license terms....

---

### Post by rickg on 2006-09-03
The SF binaries are not redistributable. The source is, however, available: 

[http://www.getswiftfox.com/source.htm](http://www.getswiftfox.com/source.htm)

That page says:
"Binaries provided by getswiftfox.com are not licensed MPL and therefore are not freely distributable. The license to use Swiftfox extends to the user that downloads Swiftfox from this web site. No one may repackage or redistribute Swiftfox binaries in any form.

Source code is available. Swiftfox is trademark Jason Halme and as such any unofficial builds need to be named differently and can not use the Swiftfox brand. "

---

### Post by DrMilo on 2006-09-03
> **Surf Man said:**
> [http://www.getswiftfox.com/releases.htm](http://www.getswiftfox.com/releases.htm)

I don't see where they are charging and it is supposed to be streamlined for each cpu type. I am wondering if some of the configs mentioned in link there are good to use in the setup for Firefox the setting that you can toggle when you enter about:config in the address bar. Anyone got any tips for speeding up Firefox?

This seemed to work. Just c+p his code.

[http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)

---

### Post by drtvasudevan on 2006-09-03
swiftfox becomes swift removing some functionality also.
it did not speed up my system. that was expected. not all benefit from such customisation.

firefox is not to be removed.let it be.

---

### Post by Drakkor on 2006-09-03
I thought it significantly speeded up web page loading........ check this out
[http://www.linuxextremist.com/?p=100](http://www.linuxextremist.com/?p=100)

---

