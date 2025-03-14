# Verses Unplugged

**Verses Unplugged** is a humorous multimedia web series that transforms popular song lyrics into AI-generated storytelling. Each episode presents the lyrics through synchronized text overlays and exaggerated, animated caricatures of the artists. Episodes are published on Instagram, YouTube, and TikTok under the **Verses Unplugged** brand.

- **Video:** 9:16 aspect ratio, 720P resolution (720 × 1280), 30 fps, encoded in **libx264**.
- **Audio:** Stereo, 48 kHz sample rate, encoded in **AAC-LC**.

## Episodes

Each episode consists of the following attributes:

| Field         | Description |
|--------------|-------------|
| **artist**   | The name of the performing artist. |
| **title**    | The song’s title. |
| **description** | A humorous summary of the episode’s narrative and visual interpretation. |
| **text**     | The song lyrics, structured into verses as an array of lines. |

## Figures

To maintain visual consistency throughout an episode, each character is defined as a **Figure**. When a character appears in multiple variations (e.g., **Young-Eminem** vs. **Mature-Eminem**), each variation is listed as a separate **Figure**.

| Field       | Description |
|------------|-------------|
| **name**    | A capitalized, hyphenated name (e.g., **Elton-John**, **Young-Eminem**, **Mature-Eminem**). |
| **prompt**  | An extensively detailed description of the figure, focusing primarily on the figure’s facial features with significant depth and precision.  The description must be objective, free from poetic phrasing, and designed for consistent reproducibility by image generation tools. It should describe observable attributes like facial structure, hair texture, skin tone, clothing materials, and posture.  Avoid metaphors, abstract symbolism, or emotional language unless directly tied to a visual element (e.g., 'a furrowed brow suggesting tension'). The description MUST describe the figure's appearance at the specified period/age/situation defined by the **Name** field and MUST NOT describe other variations.  It MAY include descriptions of other variations appearing in the same scene, but it MUST describe features directly, contributing to a consistent look across different variations. It MUST NOT contain direct or indirect references to other prompts and MUST NOT contradict the BrandPrompt. |

## Shots

A **Shot** is a self-contained segment within an episode, displaying a single continuous image for its entire duration. The number and length of shots vary based on the song’s structure and narrative.

| Field               | Description |
|--------------------|-------------|
| **figures**        | A list of **Figure** names appearing in the shot (e.g., **Young-Eminem**, **Mature-Eminem**, **Doctor-DRE**), or `"None"` if no characters are visible. |
| **image_prompt**   | A detailed description of the shot’s composition, lighting, colors, textures, and framing. It must reference **Figures** by name and align with the series' artistic direction. |
| **timestamp**      | The starting time of the shot (single decimal precision). |
| **duration**       | The shot’s length in seconds (single decimal precision). |
| **camera_motion**  | The type of camera movement (e.g., pan, zoom, tilt). |
| **motion_graph**   | The camera motion’s speed profile (defined in the Reference section). |
| **transition_out** | The transition effect to the next shot (defined in the Reference section). |
| **transition_duration** | The length of the transition (single decimal precision). |

## Prompts & Image Generation

The final image generation prompt, the ConcatenatedPrompt, is constructed by combining three distinct prompt types in a specific order:
 * Image Prompt: Defines the shot's unique visual composition, framing, and lighting.
 * Figure Prompts: Each describes the appearance of an individual character within the shot.
 * Brand Prompt: Maintains artistic consistency across the entire series by defining the overarching artistic direction (defined in the Reference section).

## Reference

### Motion Graphs

Defines motion behavior for camera movements:

| Graph Type      | Description |
|----------------|-------------|
| **None**       | Static camera. |
| **Linear**     | Constant-speed motion. |
| **Ease In**    | Gradual acceleration. |
| **Quadratic In** | Quadratic acceleration (2nd-degree Bézier). |
| **Cubic In**   | Cubic acceleration (3rd-degree Bézier). |
| **Ease Out**   | Gradual deceleration. |
| **Quadratic Out** | Quadratic deceleration. |
| **Cubic Out**  | Cubic deceleration. |
| **Ease**       | Linear acceleration followed by linear deceleration. |
| **Quad**       | Quadratic acceleration, then deceleration. |
| **Cubic**      | Cubic acceleration, then deceleration. |
| **Circular**   | Exponential acceleration and deceleration. |

### Transitions

Defines transition effects between shots:

| Transition       | Effect |
|-----------------|--------|
| **None**        | Instant cut. |
| **Pull Out**    | Image A shrinks, revealing Image B. |
| **Swipe Right/Left/Up/Down** | Image A slides away, revealing Image B. |
| **Wipe Right/Left/Up/Down** | Image B wipes over Image A from the specified direction. |
| **Blur / Radial Blur** | Image A blurs out as Image B fades in. |
| **Fold Over**   | Image B folds down like a page turn. |
| **Black/White Fade** | Fade to black/white before transitioning. |
| **Eye Blink**   | A quick blinking effect obscures Image A, revealing Image B. |
| **Camera Shutter** | A simulated shutter effect transitions between images. |
| **Glitch**      | A digital distortion effect shifts from Image A to B. |
| **Mix**        | Image A and B blend before transitioning fully. |

### BrandPrompt

Defines the artistic direction for all generated imagery:

> The visuals should feature **funny, exaggerated, and distorted caricatures** of the artists, rendered in a **photorealistic style** with a playful and humorous tone. Lighting should be **warm and inviting**, creating a cozy yet dramatic atmosphere with **shallow depth of field** to emphasize the exaggerated features of the characters. Backgrounds should be **simple yet complementary**, avoiding clutter to keep the focus on the caricatures. The **color palette** should be **vibrant and saturated**, with a focus on warm tones like oranges, yellows, and reds to enhance the comedic and lively vibe. The overall aesthetic should feel like a **quirky, over-the-top interpretation** of the artists, blending realism with absurdity to create a visually engaging and humorous experience. --aspect 9:16
