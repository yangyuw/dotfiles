# dotfiles
andy's dotfile
On Linux, it's a little more work.  I use Caps_Lock as the Switch_mode (SM) key and then defined that SM-[HJLK] combination to be like the arrow keys.  To do this:

xmodmap - pke > ~/.Xmodmap

Add this line to the top of the .Xmodmap file to disable the Caps_Lock key:

clear Lock

Then set the Caps-Lock key to be the Switch-mode key:

keycode 66 = Mode_switch Caps_Lock

This means to set the caps_lock to be the mode_switch key (and caps-lock when it is Shift-Caps_Lock)

Next, add the Left/Down/Up/Right to the third column of the key code record that maps to the letters, HJKL.

keycode 43 = h H Left
keycode 44 = j J Down
keycode 45 = k K Up
keycode 46 = l L Right

This means that for key 45, print "k" when the key is pressed, "K" when it is SHIFT-k and Up when CapsLock-k is pressed (since CapsLock is now the mode_switch key).

Once you save the file, load it with

xmodmap .Xmodmap

Most current desktops will load .Xmodmap when logging in.
You can find out what keycodes maps to what by using xev.
