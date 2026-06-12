---
title: "[SOLVED] getting an internet connection working &amp;amp; loading new updates"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-04-18
Hi guys, 

seems this is a common question, So I thought I would post what worked for me, after having to go through a number of different questions. If your connection is not working after an initial install (I am a gutsy gibbon user, this may be different for other distros) 

Open System > Network tools, and try to ping a site or two, (ie google.com) if no result. follow these steps

1st disable ipv6 in firefox by opening browser, typing [COLOR=Blue]about:config i[COLOR=Black]n the address box when it loads, type in the [COLOR=Blue]'filter[/COLOR]' box, [COLOR=Blue]IPv6[/COLOR], press enter, you should see one line that reads[/COLOR] network.dns.disableIPv6  [COLOR=Black]and double click to re set the value to [COLOR=Blue]True [COLOR=Black]and close the browser.

2nd open a terminal and type [COLOR=Blue]sudo gedit /etc/modprobe.d/aliases
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black][COLOR=Blue]a[/COLOR]nd look for [COLOR=Blue]alias net-pf-10 ipv6  [COLOR=Black]and add [/COLOR]off [COLOR=Black]to the end of the line Save it and close.

3rd type[COLOR=Blue] Sudo gedit /etc/apt/sources.list[/COLOR]
and uncomment all the [COLOR=Blue]deb[/COLOR] lines. which were commented out on the install because the program could not find your internet connection. [COLOR=Blue]Save the file. [/COLOR]

4th open System > administration > Synaptic and click the settings tab. make sure the boxes are all checked for the canonical repositories, and uncheck the CD one. Click on Third party software and check the two boxes. (you may add others later) Next use the [COLOR=Blue]find the best server[/COLOR] button to locate a good mirror/ server and accept the choice. 
 To check the network connection open System >network tools, and go to ping and try pinging google.com 

If all is well, use System > Update Manager 1st to install all current updates and then get to work installing the packages you want through synaptic. 

Hope this works for you. (I was a newbie three weeks ago, there is a learning curve but the OS is tops) :guitar:[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by talsemgeest on 2008-04-19
Don't forget to mark this thread as solved...

---

### Post by tropdoug on 2008-04-24
excellent point, but the site seems to have changed, I am not seeing the ;solved' option when I click in 'Thread tools" anymore, and the search options seem to have changed too. Can U tell me where to find the 'solved' option now so that I can mark the thread.

---

### Post by talsemgeest on 2008-04-24
I'm afraid you will have to wait to do it, the admins are taking time to re-impliment some of the old things, like "solved" and the thanks.

---

### Post by billbog on 2008-04-24
Could you tell me how to "uncomment all the deb lines which were commented on in the install..."

---

### Post by jualin on 2008-06-02
to uncomment the deb lines simply take out the "#" symbol and that should make the trick. I dont know if probably now you figure it out since you asked a month ago. Sorry for the delay buddy!

---

