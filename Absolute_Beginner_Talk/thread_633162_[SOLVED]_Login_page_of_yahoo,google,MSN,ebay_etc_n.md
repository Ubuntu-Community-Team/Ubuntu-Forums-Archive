---
title: "[SOLVED] Login page of yahoo,google,MSN,ebay etc not accesible"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by ashwinhgtx on 2007-12-06
I'm running Gutsy/XP on a ThinkPad R60. I connect to the net by wired LAN through a proxy server. The login pages of yahoo,gmail,MSN,ebay etc are not displayed by Firefox. I can use yahoo.com but i can't sign in. same with the other sites.I can access all the other websites like wikipedia, bbc etc. So my proxy configurations are correct. This is what i get from Firefox.

Unable to connect

Firefox can't establish a connection to the server at signin.ebay.in.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

I can login to ubuntu forums and sites like rediff though. The strange thing is that Firefox in XP also can't connect to these sites even though IE and Opera can. Opera in Gutsy shows the same error as Firefox.
Help would be really appreciated as i **hate using XP** just to check my mail or upload to Flickr.

---

### Post by irish_flu on 2007-12-06
Check out the URLs of the sites you can't get to versus the sites you can.

Perhaps the pages you can't access start with https://

while the pages you can start with http://

Note the "s", these are sites using SSL, probably over port 443 instead of port 80.  I'm not sure what the answer is, but I wonder if that has something to do with it....

---

### Post by ashwinhgtx on 2007-12-06
yes you're right they do start with [https://.](https://.) So why am i not able to access SSL enabled pages?? Can anyone help me out?And why does everything work fine in Opera and IE in XP?

---

### Post by Teknyk on 2007-12-06
I was almost going to ask if you are using a router that was blocking port 443 but then I saw you can get to them with Opera and Internet Exploder.

Do you have any addons in FF that could be blocking these sites? If you have any try disabling them and see what happens.

---

### Post by ashwinhgtx on 2007-12-08
I only have McAfee SiteAdvisor as addon. I tried after disabling it but it's still the same.I can't access the FF addon site as it uses SSL. Opera in XP works but not in Gutsy.

---

### Post by Teknyk on 2007-12-08
So you have:
XP - 
IE = Yes
Opera = Yes
FF = No

Ubuntu -
FF = No
Opera = No

Because FF fails in XP as well, I wouldn't think it was related to Ubuntu unless you are sharing FF settings across both OS's somehow? (I don't know if that is even possible, anyone else know?)

Did FF work in XP prior to installing Gutsy?

Just a shot here but is it possible to bypass your proxy and test?
Also can you try another browser like Konquerer?

Anyone else have any ideas?

---

### Post by Winterdream on 2007-12-08
Maybe you've disabled SSL?

In Firefox, go to Preferences, Advanced, Security.  Is "Use SSL" ticked?  Check the same on your XP.

---

### Post by CaptainInsaneO on 2007-12-08
Check your proxy server... I'm thinking they might have blocked SSL or don't even have it running.

---

### Post by ashwinhgtx on 2007-12-09
SSL is enabled in FF. If my proxy server is blocking SSL then how am i able to access the https sites in XP? Also when i used a Mandriva liveCD FF was able to connect. But it couldn't do that when i used a Kubuntu liveCD. FF in XP wasn't able to access the sites even before installing Ubuntu.I used to be able to access the sites last year using FF in XP but it suddenly changed some months back before installing Ubuntu.

---

### Post by Teknyk on 2007-12-09
> **ashwinhgtx said:**
> SSL is enabled in FF. If my proxy server is blocking SSL then how am i able to access the https sites in XP? Also when i used a Mandriva liveCD FF was able to connect. But it couldn't do that when i used a Kubuntu liveCD. FF in XP wasn't able to access the sites even before installing Ubuntu.I used to be able to access the sites last year using FF in XP but it suddenly changed some months back before installing Ubuntu.

FF stopped working in XP even before you installed Ubuntu?
I stand by my request that you try without your proxy just once. (if possible) I realize that because it works when you are on XP that you should reasonably expect it to work using Ubuntu as well. In my experience with troubleshooting I have learned to not rule out anything unless it can be completely removed from the equation.

If you still can't reach those sites after bypassing your proxy then you will know without a doubt.

---

### Post by drenalinejunki92 on 2007-12-10
hey 
try downloading firebug addon
i had the exact same problems and this fixed it very nicely



[https://addons.mozilla.org/en-US/firefox/addon/1843](https://addons.mozilla.org/en-US/firefox/addon/1843)

hope it helps
-dren

---

### Post by ashwinhgtx on 2007-12-14
I can't disable the proxy as it's setup by my university. How is firebug going to help me?? Anyway i can't access the https link for firebug.

---

### Post by rkd on 2007-12-14
Are the proxy settings in Firefox set by you manually or by giving a URL for automatic configuration?  If you set them up manually, double check that you got the proxy settings for SSL correct.  If you get the proxy settings via automatic configuration from a URL, perhaps it is time to ask your University IT people whether their automatic proxy URL works properly for Firefox (maybe they have a different URL for Firefox than for Internet Explorer).

Are there other people on campus who use Ubuntu (or any Linux)?  If you can find some, see whether they can connect to the sites that you can't reach.  If you can't find other Linux users to check this, try finding Windows users who use Firefox and see whether they can reach those sites.  If everyone is having the problem, you might be able to get together as a group to persuade the University IT folks to find and fix the problem.

A way to experiment without the proxy might be to carry your computer to a friend's home and plug it into their LAN.  That might be more trouble than it is worth, unless you find that you are the only one on campus that can't get Firefox to work for those sites.

---

### Post by Teknyk on 2007-12-14
I am going under the assumption that you have already made sure others CAN reach SSL sites using firefox.

I know you have disabled site advisor and tried but how about shutting it down and uninstalling it completely. (if possible)

I never have been a big fan of McAfee or Norton because I have seen them cause to many problems.

---

### Post by ashwinhgtx on 2007-12-14
I tried out the portable version of FF using PortableApps in XP. It worked beautifully. I set the proxy configurations manually in all my browsers. I did the same in the portable version.

---

### Post by ashwinhgtx on 2007-12-14
SOLVED!!! My settings for the SSL protocol were wrong. Thanks my friends. I'm so sorry for being so dumb. I thought it was FF's mistake. My friends used to criticise me saying that it was Ubuntu's fault. They've stopped that. I'm pretty sure that i'm the only one running linux in my university.:KS:KS:KS

---

### Post by Teknyk on 2007-12-14
Always feels good to solve a problem like that doesn't it?

Glad your back to normal.
Can you mark the thread solved under thread tools?


Oh and when they get slammed with the latest virus....make sure to tell them it's all Ubuntus fault you DIDN'T ;)

---

