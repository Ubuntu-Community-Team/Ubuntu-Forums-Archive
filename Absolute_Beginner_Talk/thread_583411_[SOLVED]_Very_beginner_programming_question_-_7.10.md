---
title: "[SOLVED] Very beginner programming question - 7.10"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-10-20
Okay, it's been YEARS since I did my last C programming, and I don't really remember much at all.  I tried to write a simple programmer (okay, more than just hello, world).  At any rate, it can't find the standard header files.  I just put in the following:

gcc myprog.c  -o myprog 

What do I need to do so that string.h, stdio.h, etc., are all found?

Also, I want to use the libusb package, but I believe I need the libusb-dev package, which no longer shows in Synaptic Package Manager now that I have installed 7.10.  How do I get that package?

Thanks in advance!:)

---

### Post by Vonnegut on 2007-10-20
Hey-o! Can we see the source code for the "Hello, world! " program?

---

### Post by anewguy on 2007-10-20
Well, it's an exact copy of the libusb sample from one of the websites.  While it wants to talk to a different device, I wanted to start with this just so I could get compiling and linking down first.  I will be changing all of the device-specific things to try to talk with a CVS camcorder since the existing programs for doing so have been "broken" since one of either the kernel or libusb updates.  That said:

/*
 * Set LED - program to control a USB LED device
 * from user space using libusb
 *
 * Copyright (C) 2004
 *     Greg Kroah-Hartman (greg@kroah.com)
 *
 * This program is free software; you can
 * redistribute it and/or modify it under the terms
 * of the GNU General Public License as published by
 * the Free Software Foundation, version 2 of the
 * License.
 *
 */
#include <stdio.h>
#include <string.h>
#include <usb.h>

#define NONE    0x00
#define BLUE    0x04
#define RED     0x02
#define GREEN   0x01


#define LED_VENDOR_ID   0x0fc5
#define LED_PRODUCT_ID  0x1223

static void change_color
        (struct usb_dev_handle *handle,
         unsigned char color)
{
    char *dummy;

    usb_control_msg(handle,
                    0x000000c8,
                    0x00000012,
                    (0x02 * 0x100) + 0x0a,
                    0xff & (~color),
                    dummy,
                    0x00000008,
                    5000);
}

static struct usb_device *device_init(void)
{
    struct usb_bus *usb_bus;
    struct usb_device *dev;

    usb_init();
    usb_find_busses();
    usb_find_devices();

    for (usb_bus = usb_busses;
         usb_bus;
         usb_bus = usb_bus->next) {
        for (dev = usb_bus->devices;
             dev;
             dev = dev->next) {
            if ((dev->descriptor.idVendor
                  == LED_VENDOR_ID) &&
                (dev->descriptor.idProduct
                  == LED_PRODUCT_ID))
                return dev;
        }
    }
    return NULL;
}

int main(int argc, char **argv)
{
    struct usb_device *usb_dev;
    struct usb_dev_handle *usb_handle;
    int retval = 1;
    int i;
    unsigned char color = NONE;

    usb_dev = device_init();
    if (usb_dev == NULL) {
        fprintf(stderr, "Device not foundn\n");
        goto exit;
    }

    usb_handle = usb_open(usb_dev);
    if (usb_handle == NULL) {
        fprintf(stderr,
        goto exit;
    }

    usb_handle = usb_open(usb_dev);
    if (usb_handle == NULL) {
        fprintf(stderr,
             "Not able to claim the USB device\n");
        goto exit;
    }

    if (argc == 1) {
        fprintf(stderr,
                "specify at least 1 color\n");
        goto exit;
    }

    for (i = 1; i < argc; ++i) {
        if (strcasecmp(argv[i], "red") == 0)
            color |= RED;
        if (strcasecmp(argv[i], "blue") == 0)
            color |= BLUE;
        if (strcasecmp(argv[i], "green") == 0)
            color |= GREEN;
        if (strcasecmp(argv[i], "none") == 0)
            color = NONE;
    }
    change_color(usb_handle, color);
    retval = 0;

exit:
    usb_close(usb_handle);
    return retval;
}

---

### Post by Paul820 on 2007-10-20
Did you install build-essential?

> sudo apt-get install build-essential

libusb-dev is in the repos, i wonder why you can't find it.

---

### Post by anewguy on 2007-10-20
> **Paul820 said:**
> Did you install build-essential?



libusb-dev is in the repos, i wonder why you can't find it.

I knew I had to missing something - I couldn't remember what, so I checked to see if I had the kernel headers and forgot about build-essential (I needed that for some package a few months ago in 7.04).  THANKS!!!:)

As far as libusb goes, it helps if your package manager source list is correct (somehow after installing 7.10, the defaults where all "off").:)

Thanks again!:)

---

