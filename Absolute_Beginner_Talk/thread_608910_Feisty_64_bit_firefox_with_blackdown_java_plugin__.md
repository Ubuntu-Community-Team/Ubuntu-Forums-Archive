---
title: "Feisty 64 bit firefox with blackdown java plugin : Not crashing anymore !!!"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by dhruv001 on 2007-11-10
I just installed feisty 64 bit on my new ACER 4520,  and had issues with the blackdown java plugin for my 64 bit firefox.

I did install the latest 64 bit java binary for amd64 , but since that did not come with any plugins, my 64 bit firefox was still using the older blackdown (32 bit ?) plugins, availalbe  through synaptics...

Initially, i was experiencing firefox crashes, ie firefox suddenly disappearing whenever i went to (mainly chat ) sites that required the java plugin


I did the following, that seems ( as of now) to have resolved the issues..
          - changed the owner of /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so , from root to userid:users ( where userid =  login userid)
         - chmod 777 this file.. 
         - restart firefox


  Now, i am able to visit the same websites, without firefox crashing.. ( I  am kinf of new to linux, so not sure if the above really had anything do with the issue .)

       but i notice that, whenever i try to login to multiple (chat) sites requiring java plugin,

                           - as long as i  open them in different instances of firefox, i am ok. 
                          - If i try to open both of them , using CTRL-T, as a new tab within the same rowse instance, firefox crashes..

Does the chmod 777 of the plugin file have any security implication , visiting sites tha require java ?

---

