---
title: "drupal - image select (field?) with thumbnail previews and selective storage"
date: 2009-06-18
forum: Art &amp; Design
---

### Post by pelle.k on 2009-06-18
That "title" was a mouthful, wasn't it?
What i would like, is, something like the "imagefield" cck, but where image field just shows you a list of previous uploaded images, i would like
[LIST]
[*]Image previews/thumbnails
[*]Images sorted in directories
[*]The ability to upload images without creating an "article"
[/LIST]
So in essence if would like the ability to upload an image, or choose from a folder structure (of my choosing), pictures that has been previously uploaded, and each image (in a subdir) presented with a preview/thumbnail, ready for inclusion in an article. It should preferably integrate with imagecache for "live" resizing when presenting the article.
Is there any stable cck component(s) in drupal 6 that will give me this?

---

### Post by alex.rayu on 2009-06-19
There's an image field for CCK that allows upload and attachment od an image to a node. And there are text editors like FCKEditor that will allow you to both upload and browse images on the server to choose from.

---

### Post by pelle.k on 2009-06-19
Thanks for responding, alex.rayu. I'll adress my concerns below.

> There's an image field for CCK that allows upload and attachment od an image to a node.
I belive you mean [http://drupal.org/project/imagefield](http://drupal.org/project/imagefield) ?
Imagefield, does allow upload, but not the ability to choose from previously uploaded pictures, preferably in thumbnail/preview format (in the selector widget, not the actual article). The second "con" would be that you get a flat list of pictures, where i would like to select from several sub directories, since a flat list of say 500 pics would be too much to wade through.

> And there are text editors like FCKEditor that will allow you to both upload and browse images on the server to choose from. 
Yes, but that would depend on the editor to do image placement and sizing, rather than me placing and or sizing it "programmatically". Having images belong to different "field" types also would allow me (designer/administrator) to process them differently in the article (separate content and design).

---

### Post by alex.rayu on 2009-06-19
No I haven't seen an image field with a thumbnail preview.

---

