---
title: "KDE Installation Problems"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by OldGrey on 2007-04-04
Hi,

I have tried to install the KDE desktop using the "Psychocats" instructions:

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

All goes well until the following appears in the terminal:

"Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; You have several choices for general configuration at this point.  If     &#8593;  
 &#9474; you have your debconf priority set to 'low' or 'medium', you will be      &#9646;  
 &#9474; asked more questions later.  You can always run "dpkg-reconfigure         &#9618;  
 &#9474; --priority=low postfix" at a later point if you want to see these         &#9618;  
 &#9474; questions again.                                                          &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; No configuration - IF YOU WANT THE INSTALL TO LEAVE YOUR CONFIG ALONE,    &#9618;  
 &#9474; CHOOSE THIS OPTION.  No configuration changes will be done now:  If you   &#9618;  
 &#9474; have not already configured Postfix, your mail system will be broken and  &#9618;  
 &#9474; should not be used. You must then do the configuration yourself by        &#9618;  
 &#9474; editing /usr/share/postfix/main.cf.dist and saving your changes as        &#9618;  
 &#9474; /etc/postfix/main.cf, or by running dpkg-reconfigure Postfix.  main.cf    &#9618;  
 &#9474; will not be modified by the Postfix install process.   

               Internet site - mail is sent and received directly using SMTP. If your    &#8593;  
 &#9474; needs don't fit neatly into any category, you probably want to start      &#9618;  
 &#9474; with this one and then edit the config file by hand.                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Internet site using smarthost - You receive Internet mail on this         &#9618;  
 &#9474; machine, either directly by SMTP or by running a utility such as          &#9618;  
 &#9474; fetchmail. Outgoing mail is sent using a smarthost. optionally with       &#9618;  
 &#9474; addresses rewritten. This is probably what you want for a dialup system.  &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Satellite system - All mail is sent to another machine, called a "smart   &#9618;  
 &#9474; host" for delivery.  No mail is received locally.                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Local delivery only - You are not on a network.  Mail for local users is  &#9646;  
 &#9474; delivered.                                     &#9618;  
 &#9474;                                                                           &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>   

Apart from not having the fist clue what it is on about. There does not seem to be away of selecting any of the options and pressing enter has no effect. Any ideas?

OldGrey

---

### Post by drakazz on 2007-04-04
Well, you can select "local delivery" option. At least, that's what I'd choose for a desktop system.

Try selecting by pressing "Tab" and then pressing "Enter", this should work then.

---

### Post by OldGrey on 2007-04-05
Thank you. I now have KDE as well as Gnome.

Old Grey

---

