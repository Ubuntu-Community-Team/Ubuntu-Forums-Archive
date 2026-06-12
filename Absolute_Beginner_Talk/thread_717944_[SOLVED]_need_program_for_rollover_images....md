---
title: "[SOLVED] need program for rollover images..."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-07
I used to use photoshop and dreamweaver when i used windows i need something that can do rollover images like dreamweaver can.

any help?

---

### Post by ruy_lopez on 2008-03-07
I use CSS

index.html
```

<html>
<head>
        <link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
         <a href="blah" class="link">blah</a>
</body>
</html>

```

style.css
```

a.link {
        display: block;
        background: green url(normal_link.jpg) repeat-y;
}

a.link:hover
        background: red url(rollover_link.jpg) repeat-y;
}

```

---

### Post by RadiationHazard on 2008-03-07
haha. wow. why didn't i think of that??
well thank you! :)

---

### Post by Oldsoldier2003 on 2008-03-07
bluefish also supports rolovers via dhtml

---

