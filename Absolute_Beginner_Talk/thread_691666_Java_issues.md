---
title: "Java issues"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by jsharptooth91 on 2008-02-08
For the most part my java works. When i try to load certin applications they don't load. I checked out the error console and this is what is says...

Error: uncaught exception: [Exception... "Component returned failure code: 0x80070057 (NS_ERROR_ILLEGAL_VALUE) [nsIWebNavigation.loadURI]"  nsresult: "0x80070057 (NS_ERROR_ILLEGAL_VALUE)"  location: "JS frame :: chrome://global/content/viewSource.js :: viewSource :: line 141"  data: no]

Any help on this would be awesome.  Thanks

---

### Post by cozmicharlie on 2008-02-08
It looks like you may not be using the correct java for the application.  Not knowing what application you are using it is hard to know which version of java you need.  You can check the programs that are not working to find out which java is required.  Then you can check your system to find out which java it is using by opening a terminal and typing:
sudo update-alternatives --config java

---

