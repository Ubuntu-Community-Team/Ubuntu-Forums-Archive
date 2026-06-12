---
title: "Quick question about firefox"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by ChunkOFunk on 2007-12-02
Okay, so, I want to use an image that is also a hyperlink as my background, so, I try to use the context menu, but, as you can guess, the context menus are for a link, not for an image. Any extientions I can use to rectify the situation?

---

### Post by bwald on 2007-12-02
You don't need any extensions for this.  If you go to view -> page source you can see the HTML creating the page.  Somewhere in there will be a tag similar to:

```
<a href="/some_html_page/><img src="/the_location_of_the_image></a>
```

If you open up the base URL folloed by "the_location_of_the_image" you can directly download it from there.  For example, if the website is "example.com," the page source would say something like:

```
<a href="/index.html"><img src="picture.jpg"></a>
```

Then all you'd have to do is go to "example.com/picture.jpg" and you'd see the picture, without the link behind it.

---

### Post by ChunkOFunk on 2007-12-03
Awesome, thanks for the help. Knew it would be something simple like that. >_>

---

