# Naive simple pitch detection

I whipped this app up to start experimenting with pitch detection, and also to test live audio input.  It performs a naive (zero-crossing based) pitch detection algorithm in realtime.  It works best today with whistling (which has a clear, simple waveform); it needs some severe help with more complex waveforms, even like guitar.  I'll get back to this eventually.  :)  There are much better tuners out there right now - like [Craig Spence's work](http://phenomnomnominal.github.com/).

Check it out, feel free to fork, submit pull requests, etc.

-Chris


## Tutorial added by Silvia Pfeiffer


### Note

* Chrome Web Audio API does not fully conform to [standard](https://dvcs.w3.org/hg/audio/raw-file/tip/webaudio/specification.html) - this uses [Chris Wilson's monkey patch](http://cwilso.github.io/AudioContext-MonkeyPatch/AudioContextMonkeyPatch.js).


### Step 1: Getting audio input

* open tutorial/step1.html
* what does it do?
  - access the microphone
  - set up a audio filter network ("audio context")
  - connect the microphone to the context as input
  - connect the the input to the output (i.e. speakers)

#### Take-aways:
* how to capture audio from the microphone
* what is an audio context
* how to route audio through nodes in the context
* what is the destination interface


### Step 2: Getting access to the frequency bands

* open tutorial/step2.html
* what does it do?
  - get audio from microphone into filter network
  - mixes stereo input down to mono
  - performs a frequecy analysis of the mono data on a 2048 window
  - draws the frequency data every 10ms

#### Take-aways:
* understanding filter networks (mono filter, fft filter)
* how to access frequency data
* use setInterval for drawing


### Step 3: Calculating pitch

* open tutorial/step3.html
* what does it do?
  - replace fft display with pitch analysis
  - finds zero crossings
  - calculates pitch & maps to note

#### Take-aways:
* pitch analysis can be done in real-time in the browser
* use requesteAnimationFrame for more immediate drawing
