# ZapVariant
IPTV Failover and Monitoring System

The plugin acts as a "digital repairman" that watches your live streams in the background. If a channel freezes or begins to stutter, the plugin instantly searches your bouquets for an alternative version (variant) of that same channel and "zaps" to it automatically. This ensures that even if one stream source fails, the box recovers the broadcast for you hands-free.

Features:

1. Intelligent Stream Monitoring

PTS Hardware Tracking: Directly monitors the Presentation Time Stamp (PTS) from the hardware decoder rather than relying on unreliable software "playing" states.
Clock-Freeze Detection: Automatically identifies a failure if the internal video clock stops advancing, even if the stream provider claims the service is still active.
Real-Time Polling: Executes a health check every 1,000 milliseconds to ensure near-instant detection of stream failures.

2. Advanced Stutter & Loop Recovery

"Bucket" Accumulation Logic: Uses a mathematical accumulation system to catch "infinite loops" where a stream plays for a split second and freezes repeatedly.
Slow Decay System: Prevents the failure timer from resetting to zero during micro-bursts of playback; the stream must prove it is stable before the "danger count" is cleared.
Aggressive Response:** Specifically tuned to trigger a zap when the ratio of "frozen time" exceeds "playback time," ensuring you aren't stuck watching a stuttering broadcast.

3. Hybrid Setup Protection

Namespace Filtering: Automatically identifies the source of the channel by analyzing the Service Reference.
Satellite (DVB) Immunity: Explicitly ignores channels with a Type 1 prefix, ensuring your Satellite/FTA viewing is never interrupted by accidental zaps.
IPTV Targeting: Focuses all monitoring power exclusively on IPTV service types (4097, 5001, and 5002).
"
4. System Stability & Performance

Crash-Guard Architecture: Every hardware query and service call is wrapped in `try/except` blocks to prevent "Green Screen" system crashes caused by unstable IPTV drivers.
Resource Efficiency: Uses lightweight Python calls (`seek().getPlayPosition()`) that consume negligible CPU and RAM, maintaining box snappiness.
Driver Compatibility: Designed to work across various Enigma2 images (such as OpenATV or OpenVIX) and external players like ExtePlayer3.

5. User Control & Interface

Dynamic Setup Menu: Provides a dedicated configuration screen within the Plugins menu to toggle the guard or adjust sensitivity.
Interactive Help System:** Features real-time descriptions for every setting that update as you navigate, explaining the impact of each change.
Dual Zapping Modes: Auto-Zap: Hands-free recovery when the monitor detects a failure.
Manual Zap: A dedicated hotkey to instantly cycle through variants if you personally dislike the current stream quality.


6. Specialized Behavioral Tuning
Manual Override Removal: Unlike standard plugins, this version removes "Pause Detection" for IPTV, treating any stoppage as a failure to ensure maximum uptime for users who do not use the pause function.
Auto-Restart Logic: The guard automatically resets and re-initializes every time a zap occurs, ensuring the new variant is immediately protected.

Manual Override Removal: Unlike standard plugins, this version removes "Pause Detection" for IPTV, treating any stoppage as a failure to ensure maximum uptime for users who do not use the pause function.
Auto-Restart Logic: The guard automatically resets and re-initializes every time a zap occurs, ensuring the new variant is immediately protected.
