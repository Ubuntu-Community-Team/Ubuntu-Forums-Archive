---
title: "[web design] an &lt;a href=&quot;&quot;&gt;&lt;/a&gt; question"
date: 2011-07-28
forum: Art &amp; Design
---

### Post by maclenin on 2011-07-28
I would like to be able to deploy the following "self-referential" code...

```
<a href=""></a>
```

...in my web designs, however, it seems Internet Explorer does not "read" this in the way Firefox (on both linux and mac) and Safari do....

Both Firefox and Safari will re-open / refresh the current page - while Internet Explorer...takes you to some other place....

Any thoughts?

I am thinking of substituting **href=""** with a more explicit reference to the current page - i.e. **href="current_page.html"** - but would like to be able to deploy some multi-browser-compatible shorthand, if possible.

**Suggestion to Forum Admins**: Add, perhaps, a "[web design]" or similar "Prefix" under "***Art and Design***"?

---

### Post by madebyjordan on 2011-07-28
Have you tried using a hash? I think all browsers just jump to the top of the current page using a hash.

---

### Post by BcRich on 2011-07-28
> **madebyjordan said:**
> Have you tried using a hash? I think all browsers just jump to the top of the current page using a hash.
```
<a href="#"></a>
```

---

