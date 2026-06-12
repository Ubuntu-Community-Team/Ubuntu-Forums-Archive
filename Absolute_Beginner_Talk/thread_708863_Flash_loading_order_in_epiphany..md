---
title: "Flash loading order in epiphany."
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by TheMilitia on 2008-02-26
When I visit a page that is largely flash I have problems with some parts loading on top of other parts. Internet explorer shows them fine, but with both firefox and epiphany I have this problem.

Specifically, I am having large images in the center of a page load after a drop-down menu at the top of the page. By loading last, the picture below the menu obscures the menu choices when it drops down.

Is this just a function of the site? Or can this be changed by loading preferences or something like that?

---

### Post by northern lights on 2008-02-26
What version of Ubuntu are you running? What window/desktop manager? What graphics card (or more specs)?

For now, I am assuming it's Gutsy & compiz. If that's wrong ignore what follows.

Gutsy ships with compiz0.5.2 (don't quote me on it, whatever it is, same thing), in the combination with your graphics driver, it doesn't get along with flash too well. It's very unlikely a browser related issue.

On a buddy's laptop, the new Hardy alpha5 release with compiz0.7.0 (again, don't quote me), flash worked like a charm. However, I would strongly advise you not to follow you're urge to try that one out at this point.

Rather, the default window manager, "metacity", should handle flash in Gutsy well. So whenever you wanna browse websites with important or large flash content, open a terminal and type ```
metacity --replace[CODE] when you wanna go back to compiz, run
```compiz --replace[/CODE]Not very elegant, but it should do the trick...

---

