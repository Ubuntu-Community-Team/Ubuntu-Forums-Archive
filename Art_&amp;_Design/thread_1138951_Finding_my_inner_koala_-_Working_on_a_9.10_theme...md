---
title: "Finding my inner koala - Working on a 9.10 theme..."
date: 2009-04-26
forum: Art &amp; Design
---

### Post by detrate on 2009-04-26
I little while ago, I posted about [my progress on a brown theme, EarthyTonez](http://ubuntuforums.org/showthread.php?t=1123521), which I'm pretty happy with it.  Recently however, I read over in the art wiki that [Ubuntu 9.10 is moving away from brown](https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Finding_Your_Inner_Koala).

I figured I'd start playing with the concept of thinking outside brown and based (loosely) on the palette, here's what I've come up with in my vision of a darker theme for Karmic Koala.

[[IMG]http://pics.nexuizninjaz.com/images/5wb5xo1fhe8qbqank619_thumb.png[/IMG]](http://pics.nexuizninjaz.com/viewer.php?file=5wb5xo1fhe8qbqank619.png)

I based it on my EathyTonez theme and customized the colors further with gnome-color-chooser.  This theme is not quite ready as I've only been working on it a short time but if you're interested, and know how to use it, you can download the [gnomecc file here](http://z.nexuizninjaz.com/linux/themes/karmy.gnomecc).

---

### Post by Sand &amp; Mercury on 2009-04-27
Just FYI, the move away from brown is not set in stone as part of the plan. They're just considering it.

---

### Post by Merk42 on 2009-04-27
> **Sand & Mercury said:**
> Just FYI, the move away from brown is not set in stone as part of the plan. They're just considering it.

Which would involve a new theme, and we all know contrary to what is being said, we aren't going to get.

---

### Post by Giant Speck on 2009-04-27
Purple and green don't look good together.

---

### Post by detrate on 2009-04-27
> **Giant Speck said:**
> Purple and green don't look good together.

In you're opinion maybe but they are actually part of the cool side of the color wheel, bordering on complementary: [http://www.lowes.com/lowes/lkn?action=howTo&p=HomeDecor/ColorScheme.html&rn=RightNavFiles/rightNavHowTo](http://www.lowes.com/lowes/lkn?action=howTo&p=HomeDecor/ColorScheme.html&rn=RightNavFiles/rightNavHowTo)

The theme is really starting to grow on me, I will continue to refine it and maybe try out a few other possibilities.  Any suggestions are welcome :)

---

### Post by Merk42 on 2009-04-27
> **Giant Speck said:**
> Purple and green don't look good together.
Why So Negative?
[img]http://www.nercm.com/wp-content/uploads/2008/07/the-dark-knight-the-joker-16-scale-deluxe-figure.jpg[/img]

---

### Post by Giant Speck on 2009-04-27
> **Merk42 said:**
> Why So Negative?
[IMG]http://www.nercm.com/wp-content/uploads/2008/07/the-dark-knight-the-joker-16-scale-deluxe-figure.jpg[/IMG]

Do you want me to lie instead?  The theme itself is nice.  I just don't think green and purple are the best colors to put together.

---

### Post by Merk42 on 2009-04-27
> **Giant Speck said:**
> Do you want me to lie instead?  The theme itself is nice.  I just don't think green and purple are the best colors to put together.

No no, my reply was a joke, though it was showing that purple/green has been around before.
I feel the same, I don't think purple and green look good *in this particular theme*

---

### Post by Marlonsm on 2009-04-27
I don't think Ubuntu will ever move away from a Brown/Orange based theme, as it's what makes Ubuntu looks unique.

What might happen with Karmic is a redesign of Ubuntu, but not going to another color scheme. Maybe using more neutral colors but keeping Orange/Brown for details. Think themes like Dust and New Wave in Jaunty.

---

### Post by detrate on 2009-04-27
> **thereplicabags said:**
> the picture look good, and where can get this soft?

As I said, this theme is based on my EarthyTonez theme, so you'll need to download that first.

[right click save as this](http://z.nexuizninjaz.com/linux/themes/earthytonez_0.8.tar).  Extract it to your home directory.

I'm working on another fork of the Dust series, so you'll need to download that if you want better looking titlebars (this is a slight alteration I made after the screenshot was taken).

[Download Dust Purplez](http://z.nexuizninjaz.com/linux/themes/Dust_Purplez.tar) and extract it to your ~/.themes directory.


For the color palette, you'll need gnome-color-chooser.

[code]apt-get install gnome-color-chooser[/url]

Download this: [karmy.gnomecc](http://z.nexuizninjaz.com/linux/themes/karmy.gnomecc) to your desktop.

Open gnome color chooser >> file > open > ~/Desktop/karmy.gnomecc


Now your theme should look like the picture below:

[img]http://pics.nexuizninjaz.com/images/1abixryyntnggl5atx.png[/img]

---

### Post by Dwood15 on 2009-04-27
Your theme isn't bad, I would just work on changing the purple.

---

### Post by Giant Speck on 2009-04-28
Please tell me how you got Ubuntu Forums to look like that!

And please tell me it's nothing more than a Stylish theme!  I want it!!!!

---

### Post by detrate on 2009-04-28
> **Giant Speck said:**
> Please tell me how you got Ubuntu Forums to look like that!

And please tell me it's nothing more than a Stylish theme!  I want it!!!!

Yes, it's a stylish theme but it's incomplete.  I'm only about ~70% done with it.  If you don't mind some things looking bad:

```
/*

Brown Ubuntu Forums by Tyler Mulligan of www.doknowevil.net

Notes: Theme is only ~70% complete, I started by going from the top down on the
most visited pages, no images have been updated yet except the header and some
pages may look bad.

*/

@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("ubuntuforums.org") {
  body {
    background: #3D3223 !important;
    font-family: verdana, arial, sans-serif !important;
  }

  td.vbclean_topfg[align="left"] a {
    margin-left:4px !important;
    display:block !important;
    width:202px !important;
    height:55px !important;
    background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMoAAAA3CAYAAABNadVvAAAAAXNSR0IArs4c6QAAAAZiS0dEAP8A/wD/oL2nkwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9kEHBUjNeRde3kAABWYSURBVHja7Z13cBzXfcc/u3sddyiH3ohyBAgWgE2QSJoUJUqkLIked41iyVI0tmPPRGmyZ5x/MpM/MpNk7LEn9mTGcYlsWZaLEimW7USWZIlNYhfYxAKiEEQjDoe7A6633fxxwBHA7TWAIAHpvjPg8Hb39t6+977v198K//SXDyvkkUceaaFZzo3Te8LYTo5Q3udGF4oRLNAy2mqlZ1stiEJ+9PLIE8XkCrLjpQuAwAwlDL4IjV1jNHaNceDLG4nqNfkRzOO2QFyuDdv2m0tzSDIDAVCAHS9dzI9eHh9totRcdCBFZYQ0jdb7I5gd/vwI5vHRJUrdhfGM1yiAxRHIj2AeHw4bpSHmojM2TLnixaDE0BJDIgYIKIpAVBAJIRESJH6ovyfO3piCMq1mpWW5LK+Yjv7paycZGZ9EEkUe2rGGTWtq87MvDYKhCD985Ri+QJhii5GvfnY74h104CwJUSplD7ui17DJLjTICQkgzLE0AEFBIoaeGChQK08yLBYxtroEy4n00kIAPFbTihj03x64QM+gI/H5v946R31lMaXFBXlGpMC3fnaAUCQKgC8Q5jsvHuQbT9334VK9amQPa+SJBEnIQjoAbI9eB6C/sxpFiJNLDTIgCzBVuTKI8v6l4aRjJy8O5tmQAh5fMEGSGbg9AWIxeaUTRcGovflgXZoaPOhyvINCk+xKfL68qz7h4VJr9HtPbABhZcRSYioq4rjTm2dECthT9M2NCc/KJYokynxl1wc8dtfVOcd/rWtHIbVUSFalBHTIPB46C8BQewWnPtlC2KRN3EcWwF+k550vbyRQpF/Rk0FW8gkRqRcWJesFZ0XYKBpR5rm9XWhEBQGwFgRx+gwAjIkWhoQi6pXJnO5pU1zsjvRxUNuMq66QQ890TIscZcVIkDw+fFiURHlubxcaSU7M3yfvuTLn/Iu6jQtQ4uBjsQH+JnAEoxKeJXKEOc6CPPJYERLl7x7sQivN8mUJYDFE6Kh1cG64LK5eCCInpFo6Y8NkKwuE6X/NQpTnQu/hR0NA0OJFRyEhDEoEoxLjqKaet7W2/AjmsXyJ8pVdFzDpYsnSQIFH268liALwpraFLbERNNPWypBQyLhoIoqESQlTq3goUoIJw30+oUxEMSlRSgncPC/AtuggvaKVAanklnREKBxFr9Pctu+pwR8MYzLoFnWPYCiCQa/N+XvhSBSddvHPEQhG0GolNFLuysrYhIdj5wdwTamHBg6c6sVs1KEAzbWlbG6rvW3jmvMdNtRMUGEJoigKwjybQRAAQeGhdQP88WJD4vgLus3ICIyJFnX9T5GxyU7uiV5nlTKVUvoI8z48GTnLt8SdhIWFD/D1Gy5+9tqphDvygbtbuL9zdcbvHe7q44/vxVVNnVbiyUe30lxbmoMTRGTYPsmBU730DI4Tid40VHVaidZV5Tyycy2FZkNW9xsYdfH8b08QnXahfur+Ddy1rj7j9w6e7uXNY90AGPVavvq57ZTlEN859H4vH/SOMTo+leSgsBaaaK4rZffWZkoK07vy+4Yn+M//OZH2mu6BmxkbXZeHcbi97N22RvXaayNOXvj9KcKR+IL+0I417NrcnNXzvHE03h8GnYZnPnk3tRVFSHvubvnH7I33GF/aeWnark4xnRWB2hI/7w+UE4lJAHgFPT4htZdKEQScoolzmmoGhGJsshMdsbTR+RkJVKiEuCKVL5goP3j5KP5QJPG5f9jJri3NSGL6FfHHrxyb46XpHhhPORBvn+xJOjbh9nHy4iAOtw95npcnJivYXV7ePXsNURRprLFmfI5vv3BgzkS9fM1O5/pVaVdTXyDEz353KvE5GpM58cF17rvLlnp8p9E76OC7vzhI7+AEHl9I1bsZCEUYGZ/i6LkBojEZW31Zyvu9c7KHUUdutueY08O9W9TV7+/98nCCJPH2TrB7qy1tdN8XCCf1R8/gODs2NuVmzO9pG87ofBIEUBSFysKFJSxel4r5N8MOrgtFCeM+nT3TLt+gRF54cqTHH0o6NjuKrob+YWdSu3yBcM5Oi2zw1vFuXn7zbNpr7E71CeZw+9J+78yVERX1WUnpnp29sj//2kly8XAfer+Pn7x6POX51obcF7u1TZUpz0UiyaZB15XhtPeb8gaTjrk9wdy8XkZtlM7GsbQkUZT43w8OtdPnKFqUrvtz/Wb6RGtGJ4CCwAPR3gX9RqrJrdZhcwYhGlO3D8KRJTEkz3aPcPB06mdcaNxhtrqXLYOD4Qgv/P7Ugp6jf8TJW8e71VX61dU8tm8jlaUWilKom8UWI+UlBTTXlfLYvk189oGOnBaiQDD9+ARCkcUb82uqXKRLRJmxWV7pak7EUhaLX+k6+FLoJFWyL+VPC8Aa2bGg+6civbDAeI2AsKA2bO9oZFVVMa6pAAdP9xIMR5PVtxNX2b31znv5vvfSkUV9/+DpXu67a7Wqsd/RUkNHSw3dA+OqZHxs30ZWVS3CebOIMFzWRHmgbSit2iUIAnaPgUuj1ls6MC/qNvGN0LsZe2B79DpHNatWlMtxS1stn5m3Ku7a0szl/jFe/N/3k6TGHw5f5NFd6+5Ye73+EFM+dWnbsqqMxx/ajCgKyLLC0Jib5187qap1vP7uZfbfu25FjVXWqtcbF+szBsZ/cuTWP3xI0HJYasio76+N2Vlp+EwK1aGtqZKWVcmG77mro3e0vVcG1OuENrbW8PQnOtHrNGg1EnqdBlt9Gd/88z2q1x87P7DixmoOUcplL4+Hz/Js8Ch/HXiPJ0NdNMWcAJwfLuPVrubEqjAfQ64CZGVp6sBOaOoyGvVWZWUVcT2ysy3t+Scf2ZqTDn07cKFHnaif3rNB9bilQM+mNTXqC6CKerkiiHJXdIivhE7RJLsoIoRFCFOvuPlC5Bz7wvGEx4ujVobdBUmSRUHhWF/VkjUyKGgZFgrTXqNXYggrKNFwTWNF2vOSJFJSaJxzTJaVlKrP7cCwPTlvz1poQiNJKb9jqyvLySGyrIlSK0/yULQHQZgrYsRp66dTHmZTNO5KfPFYK8nOFIErYyVL2tAuqTqtVFEEaJyVpr9Uxnf6yZ39/bQaKeM1xWZj0rFrI847Nln8Kl6j0uL0gcQii7pjJ7aCqlMTxvzOyEDa4J4M7IwOcEZTQ1QWiSkCgqIkJIsnqF3yhvZJVv6ELSVZBBR8Qm7pH1qtdGs7U8r+fmIWnjW1Seb2LLGKmePaYcyQLqNLsSBkitUsS6I0KO60/SMCRYQSPRmJiWikm6LTH176/bW8gp7jmvpbPLEXZlMtVbwkSUKJ4pI+RzQWy5or0RTVhVKG304lOZUlVpPViv7kRZBTBNAouemLkZg0pzNl+cNVJ+INhNKeD0cWr19nM1HUsgbUkiZTTUZ/MH22gJqdcKvV0VRYamNeUElVyZQ9kc5ZIgI4xMxJcCFuDoZJF5nDVoM2umJJoaYCjU2kL9N1TflzWtUNKjtaZqN6qGUI1JQXZnV/gAl3+tSeSZX7C8LCA67LCWrS2O7MNK4B1f5IqF5dUg17Iz0p4ySKojAgFc98QkKZs+4Um8JL/uDWwUm2vNaTVtSe29fEWEtuAU+zSZ/kSbrcnz4mc7FvTGWyptbVrYUmRsan5hy7MeGh2GJM+zvjLp8KUZJTgww69d/uHhhPmwntnPSrTAxh2RaS5tIsjSQmScxMRLl8LXnci6YdKiLASU0dY6JZnSSAHx0v69oB6GywI0rzO1fBWrC0bsvKHneis9T+ANxV5pzvq+a1iclyypqIWEzGoTKBLabU2dG1FcmT+/+OXErbriNn+pM8Q4Y0ey2rpcYPjrlVpd+MGjKfvACFZsOylSj+YPa2oU7FUePxBfGlUKu9/pCqR7Gy1HKTKAA/0d/FRbE8iSX9YgnfN2yLezi0UfatH1QNOG5vWtqocd1FR9oVRQFCltyLnlLVkHz3FwcZm7frh3PSzz8//ydVz1tDdWr3eMuq5MzYiUk/51NE2n2BEG8evZJ0vLo0dSwpVe3JD//7WJLkGHd5+fYLB1Sv37W56Y4TwmRQl5DjGbKhZ6OjpVp1jvzrT99JyrZ2Tfn599+op0nZ6kpvql4zeFW3nleBGnkKEZkhsfjmaqaJ8ld7zqjneykCrVVu/nBhaTquvDd9fESBBe/K8rFNTfzpxNWk47Ks8P1fHaHAqKPSamZi0q+q08/g4x9LHWlf16yeDv7rN84wbJ/k7vZV6DQS0ZjMsH2SX77epXr9Y/s2pfyNDaureP29y6oOge+8eBBLgZ6yogIckz48vlBKvb5z/Z3Pl6uwqmsGh073sqm1Bo0kEghF8Acj6HUaVWn60I42Dnf1q47r9355JN4fxQU4XD5Vp8l8wqnK8hExeeX6+r4zKZMiBQFMuhj3tgxz6Oqt3yq07dBgxiKuyYqFbYan00rs3trMwdN9KVWUvuH0Qb57NqzK6KL9/N6NqnUlR870c+RMf8Z22upKsRSkXgyKLUY2t9XSdVm95sLjC6UkyAw6N9SzHKDTahLJlfNVr395/m3VBURNgnS0VKfMj8umPx64uwXztEqdtQO+63oZmSp1dthGyL4kKTu0vDuEwR/JYMgp9N1ds+Df2LttDYUFCysNKC0y8Ynd6zNet7G1RtVWyVYVeeaTd2e87lP3b8gqkKmGqlIL+xeQmSwtcD/gTAtLLnsHnOseSSmBrYULW0AtJv0cR0jWRDl5rSLjW64kUeDrD565dSpXn4vGM2PpU1cAb4kRf/HiamC+/tRuSoty69TqskL+9ol7s77+a5/bTnNtbl65wgID33xmT5aTVuQf/mJvWqOfFPbVs4/vzDix1UhRVZY+B2/GGJ6PTBH9p/ZvzZ7kZZaU55774m7KS3Jz8pSXmPnG0/fN7dtsa+b9YS0dtQ70mlha96FGUthUN87JgUoWUylT0eti4+t9Gd2CAgrdO+rwli9uH2JRENje0UhNeSEX+8bS7uSo1Yg88fAWHt65NicPkSAIbG6rw1ZfRveAPW3gUhDi6tpn9rQjitlH3iVR5N4tNkqLC7jcb0+7yBQYdXzh4c0pN2hIcnzUlfL+paE5ffaFh7dk3GU+HIlx/YY78bmpxsq2jsb0K3qBgaba0pSq5Ax2b7Wxd1tr2mu2tTdQVWbhUr897bjqtBJPPLKVR3etTZLMQi4vOy0tCPC13R+kLeCaOffC0TUMuiwLmrStRwZpOGvP+OoHBYWgWc+Rp9tvuZ7scPsYd3nx+sNEojF0WokCo46KEvMt24Xe7Qlgd3rx+kMEwxF0Wg0FBh2lxQUpDdpcYXd6cbh9+AIhIlEZvVbCbNJTbjUvSC254ZhiYNSFXqehfXV1xhSWGfQMOhh3eikpMtGWIXN6Pq7fcOGc9OMPRhCEuDQqMhupryrKKb8uMa5OL95AfFy1GgmLSUd5hnEVcn0r8Be3XWaV1ZtWFfIEtHz/nVm7RMpKVi8nrbzqZM2RQfT+aFbvR1GAU59eg7vGTB55LCVyzmb8+bE2/v7jp5HEZH7JSnxy/+jwXOO285UrGD0hBtsrcFebiejjq4AoK+h9ESp6XdRccSakRLYZR8Nry/IkyWN5EgXgR4fXqapgogDXnWaCUc0sg9xN0ZgPAbAdH0naEVJBmUOLmf/PXKMAsiSAAIIcJ5cCRPUSl/Y05EfwNuL3R7rTnt+/szVPlNmY8Bl544P6RJQ+vpcXxGSBnx+bG3hrO3R9FglIMs7nyw4ZJVEw5lhVyIUHG4kYb3pITK4gm393laN/ti4/c/NY3kQBODlQiSgqPLB2KCEbjvfPLQde/d4QBl9utRsiAgpw8EsbiRiSm+cvMfDuU+35kbuD+DBLjltOFIDj/VW4/Ho+v7UXb0jHge66Oeez8VzNN84B3v7qZmRN3Jtyb8swG2ociCKEYyLH+6o4O1Sen63LFLKs0DfiYmTcg3e6/sNs1FFbbqGppmSOK3lGlfv49tVc7B9n1OEhEpXZv7M1cW4+KdWOzxx7aJuND/rGuTHhRRDAVmdldZ2VUCTKhV47dqcPURRoqCpmTUPpHNd+NCbTfX2CUYeHYDiKJIoUWww01RRTaTUv/mWn3WMl/Meh9ZSY5qYDbPltN4Ks5BxJOfx0O7JGRCPGePb+85j0UZhlC+3vGKCz0c6Pj6wD8i8WWk6IyTLHLwzjnJd5PeULMeULYXf5uGd9XVLcpevKKGNO36J/v6v7BvZZ97l8zYHJoKV3yMmkNzTdRoWeISdGvYaG6pu5jGev3mDU4Z1DHIfbj8PtZ//O1lvzVmCH14jDe7O2QhuIYh2ammemZ5Yn/mIDIXM8deHZ+89ToI8mGzVAhSXA451X+dXJ1vzsXCZG/f6drfSPuHFOBdBqRDbYKqicjgWNOb2c77EzMRmgf8SFrW5udsKkL8S2DXVYC42LekV2KBzlvi2NGPUaLg846B9xc/bqDcxGXdLxwbGpOUQZm4gTbH1zOXUVhUiiyKQvSO+Qa9okWAI0nxpFEcUcby5wbUvcxqkv8dwkidqVAtjKpygxBfOzdhlh2B6vb2m3VVJbXohGEtFIIrXlhbTb4kHG4fHkDcU7bJWUFZsW/R75jtWVmE06JElkdX2cjLGYonp8fsawThcPWYy7/PSPuHF5AhSbDdy1tmbxNkoqXNlVz5Vd9VRfctBw1o7BG0YbisK0oU4KpcneHGf4rpaRzPJHgcpCPy6/IT9Dl4kx7wvEHTcV1uQId2VpXLp4VerWS4uMt6RdhbOyq/WzXoqkdnx+KXaHrZKu7lHsLh/26cI8k0HL1rZqiswGlnT7lNG1ZYyuvbkBWqHdh2Xcj94b71BZI+AvMuCuMRM23XQBF+iz85QV6KL5WfshQLZpMJk25EiVd5dNPl6FtYAHO5sZd/uZmPQz6vDiD0Y41zPGrk0NaG5nh0xVFDBVkTlP6vqEhQpLMEOngN1jzM+yZYQCoxaPP4zd5aNmXkbv2HS9utmYXfr8TD3K7FfETWWoH7kVhK0qNVNVasZWZ+WtE31MekMoirI0Nspi8cbFVYl3raSVWJMF+dm5jFBbEU+5P98zxojDQzQmE43JjIx7uNAb37ihtjy7RFmLKU6oq4NOYjEZXyDM+Z6l24j9+IUhxl2+RJtniC0KAoIg3F6Jkr3/S+DEtUruaRpLyqecyQR46UQLUVnMz85lhKaaYuxOH86pAO9fHlW1RZpqstt6t66ikEnvONdG3VwbjafoV1qXbmEcd/sZV9neqaosblst25n21qV6/vhBPbF5ZAhGJF4+baN/kW/0ymMJVBdR5J4NtbQ1lmEx6RAFAVEUsJh0tDWWqcZQUqGxuhhbXQlajYgkCdSWW9jcWr1kbd+2oY6qUjNaTTyByqjXYKsrYePq+H4HOafZ55HHRxF53SWPPLLA/wO6i0DH1pR52gAAAABJRU5ErkJggg%3D%3D);
  }
  .vbclean_topfg a img {
     display:none !important;
  }

  #header_right_cell a, .page a {
    color:#DBC4A8 !important;
  }
  a:hover, a:active, body_ahover {
    color:#fff !important;
  }
  .page, .alt1, .panelsurround, .panel, .vbclean_topfg, .vbclean_top *, .vbclean_bottom * {
    background: #846B49 !important;
  }
  .navbar, .alt2 .smallfont, #searchbox {
    color: #E7D3B3 !important;
  }
  #searchbox input {
    border: 2px solid #9A815F !important;
    background-color: #3A3022 !important;
    color: #D0B28A !important;
  }
  .time {
    color: #EEDEC3 !important;
    font-weight: bold !important;
  }

  .vbclean_fhomecat_topfg div + div + div {
    background-color:#909056 !important;
    border:1px solid #4D3C22 !important;
    color:#555528 !important;
  }

  .vbclean_fhomecat *, .vbclean_fhomecat *, .vbclean_fhomecatfg {
    background-color: #BFA173 !important;
  }
  .vbclean_fhomecat *, .vbclean_fhomecat * {
    border-left:1px solid #8C7451 !important;
    border-right:1px solid #8C7451 !important;
  }

  .vbclean_fhomecatfg div + div + div {
    background-color:#836B45 !important;
    border:1px solid #4D3C22 !important;
    color:#C2A577 !important;
  }

  .vbclean_fhomecatfg .vbclean_forumhomecat strong {
    color:#6F4400 !important;
  }

  .vbclean_fhomecatfg div + div + div a, .vbclean_fhomecat_topfg div + div + div a {
    color:#fff !important;
  }

  .vbclean_notice * {
    border-left:1px solid #B5CE7F !important;
    border-right:1px solid #B5CE7F !important;
  }
  .vbclean_top *, .vbclean_bottom * {
    border-left:1px solid #634D30 !important;
    border-right:1px solid #634D30 !important;
  }
  .tborder {
    border: transparent !important;
    background: transparent !important;
  }
  .tborder td {
    background: transparent !important;
  }
  .tcat {
    border-bottom:none !important;
  }
  .vbclean_postbitleg *, .vbclean_postbitlegfg {
    background: #B29771 !important;
    border-left:1px solid #9E815B !important;
    border-right:1px solid #9E815B !important;
  }
  .vbclean_postbitmsgfg, .vbclean_postbitmsg * {
    background-color: #BAAE9B !important;
  }
  .vbclean_postbitmsg * {
    border-left:1px solid #B8A68C !important;
    border-right:1px solid #B8A68C !important;
  }
  .vbclean_postbitmsgfg a {
    color: #4F3F29 !important;
  }
  .vbclean_postbitmsgfg a:hover {
    color: #8A7352 !important;
  }
  .vbclean_newthread * {
    border-left:1px solid #968C75 !Important;
    border-right:1px solid #968C75 !Important;
  }
  .vblcean_navbarfg a, .vbmenu_popup a, .vbclean_announcefg a, .vbclean_noticefg a, .vbclean_newthreadfg a, .vbclean_fhomecatfg a {
    color: #554730 !important;
  }
  .tcat {
    color: #CF9A55 !important;
  }

  .info_bar .alt2,  #activity_info.alt2 {
    background: #70593D !important;
  }

  .thead, .tfoot, .vbclean_bottomfg {
    background: #634A2A !important;
    color: #fff !important;
  }
  .shade {
    color:#271C0E !important;
  }

  #threadslist .alt1 {
    background: #917B61 !important;
  }

  textarea, input, select {
    background-color:#423829 !important;
    color: #C3AA84 !important;
    border:1px solid #916A31 !important;
  }

  .vBulletin_editor {
    background: #9C8464 !important;
    border:1px solid #916A31 !important;
  }
  .imagebutton {
    background: #9C794B !important;
    border:1px solid #916A31 !important;
  }
  .imagebutton:hover {
    background: #D2C1AA !important;
    border:2px solid #916A31 !important;
  }

  fieldset {
   border:2px solid #594831;
  }

  .tab_header {
    background-color:#634A2A !important;
  }
  .tcat {
    background-color:#3A3126 !important;
  }

  .vbclean_msgtags {
    color: #F3D13A !important;
  }

  #inlinemodform .alt1 .smallfont, #inlinemodform .alt1 strong, #inlinemodform .alt2, #inlinemodform .alt2 .smallfont, #inlinemodform + br + form .smallfont {
    color:#fff !important;
  } 

  #inlinemodform .alt1 {
    background: #726249 !important;
    border-top:1px solid #544939 !important;
    border-bottom:1px solid #392B17 !important;
  }

  #inlinemodform .alt2 {
    background: #5F503B !important;
    border-top:1px solid #544939 !important;
    border-bottom:1px solid #392B17 !important;
  }

  .block_row {
    background-color:#61503A !important;
  }

  #inlinemodform + br + form, #collapseobj_forumhome_activeusers {
    background-color: #322E29 !important;
    border:2px solid #CBB89C;
  }

  .vbclean_bottomfg {
    margin-top:5px !important;
  }
  
  pre.alt2 {
    background-color:#3B2C17 !important;
    color:#A1DF49 !important;
  }
}
```


Update: now with a better header image, embedded in base64 for (y)our convenience!

Update: I've gone from ~40% to 70% today.  I'll probably start up a thread for this soon now that I've just about wrangled the styles, at the cost of some CSS2 selector trickery.



I'll post an update in these forums when I complete it.


And hey, if you like the forum theme, maybe you should give this 9.10 theme a shot even though you're not in the color mix. :-P

It's not particularly my favorite color scheme (see above, I've been on brown for some time \m/(-.-)\m/) but after using it for a few days, I must say I really enjoy it.  It's a very soothing color scheme.

---

### Post by manoynmonic on 2009-06-20
I love the theme.  The purple looks good to me.  Buuuuuut...  In my scroll bars, the scroll dealio is virtually the same color as the bar behind it.  Which color in gnome-cc changes that?

Thanks for sharing your theme!

---

