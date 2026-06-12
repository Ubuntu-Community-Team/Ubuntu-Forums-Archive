---
title: "Yahoo Mail Beta rejects Swiftfox"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by David Valentine on 2007-02-07
As of today, apparently, Yahoo! is not allowing users of Swiftfox to access their e-mail using the Yahoo! beta webmail.  I get this when I try to log in:> Sorry, Yahoo! Mail Beta does not support your browser.Firefox is not a problem.

So, it seems like I need to change the way Swiftfox reports itself to Yahoo! mail, e.g., making itself appear like Firefox.  Anyone know how to do that?  Or of a better way to solve this problem?

---

### Post by borris.morris on 2007-02-07
I know that on Konquerer there is a way. Not sure about Swiftfox. I'll try it out and try to figure out a way.

---

### Post by jpeddicord on 2007-02-07
[https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)

That extension right there will do the trick (providing Firefox extensions are compatible with Swiftfox). Install it, and I believe one of the default options allows you to change the user agent to a default Firefox.

Jacob

---

### Post by David Valentine on 2007-02-08
Wow, thanks for that lead, Jacob!  For anyone else that runs into this problem, here are the steps needed:

1.  Install the [User Agent Switcher extension]("https://addons.mozilla.org/firefox/59/")
2.  Restart Swiftfox
3.  Download a xml file full of agents--I used the one available [here]("http://www.testingreflections.com/node/view/4162").
4.  Go to Tools/User Agent Switcher/Options/Options.../User Agents
5.  Click Import... and navigate to your downloaded xml file, and click Open.
6.  Choose from your now extensive list of User Agents, select it, and navigate away.

---

