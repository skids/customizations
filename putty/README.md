pterm customizations
========

My own customizations for pterm

## Why

I use terminals a lot.  I need them to work.  What bells and whistles I
need are fairly basic.  If the bells and whistles break the part I rely
on or make the code hard to maintain, then screw that.

I found that libvte kept dropping essential features of older terminal
emulators (most recently :bw: support in the newest versions.)  I looked
for non-VTE terminals that had most of the features I needed and pterm
was pretty close... except that it did not support cutting and pasting from
the X clipboard.  I use both the clipboard and the cutbuf together frequently
and while clipboard managers are nice, most of the time I only need two
and the less mousing around or hotkeys the better.

Despite the best efforts of HP, I also have managed to configure a mostly
usable "middle" mouse button on my latest laptop and this customization may
not be as useful if you have only 2. (HP still did manage to make this laptop
suck with the chiclet keyboard that does not type right when you strike
the top of the keys, but I digress.)

This patch does two things:

1) It inverts the sense of the control key for the purpose of opening
the context menu in pterm.  Just right-clicking opens the menu.
Right clicking with control held down extends the selection (a feature
I hardly ever use.)

2) It adds "Cut (to clipboard)" and "Paste (from clipboard)" menu items
at the top of the context menu.  Normal fast-select and fast-paste with
the middle button continues to use the primary selection buffer rather than
the clipboard.

This brings pretty much the same behavior as VTE-based terminals to pterm,
without the drawbacks of VTE.

The code seems to work (there might be a bit of weirdness when the clipboard
is empty after first starting up), but has not been thoroughly tested,
documented, nor run through any sanity testing tools.  Nor proposed
upstream.  Nor has the ctrl-key behavior been made optional.  If anyone
feels like doing any of those things, knock yourself out, my work is done here.

## How

Included is a patch and the entire unix/gtkwin.c file (which is the one the
patch modifies.)  Note that all work was performed in a Debian-patched source
directory.  Try applying the patch to your distro's tree.

