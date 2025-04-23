# traffic-management.
📦 Code Components Explained
1. Headers and Constants
c
Copy
Edit
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
These headers are used for:
stdio.h: Input/output functions (e.g., printf)
stdlib.h: General utilities (e.g., rand)
time.h: To seed the random number generator with the current time (srand(time(NULL)))
c
Copy
Edit
#define MAX_INTERSECTIONS 4
#define MAX_TRAFFIC_LEVEL 100
MAX_INTERSECTIONS: The number of intersections to simulate (4 in this case).
MAX_TRAFFIC_LEVEL: Maximum possible traffic level (used for random generation).

2. Data Structures
Traffic Data
c
Copy
Edit
typedef struct {
    int traffic_level; // 0 - 100
    int pedestrian_count;
} TrafficData;
Represents traffic conditions for an intersection.
traffic_level: Simulated traffic intensity (0 to 99).
pedestrian_count: Random number of pedestrians (0 to 49).
Signal Timing
c
Copy
Edit
typedef struct {
    int green_time; // seconds
    int red_time;
} SignalTiming;
Holds the green and red signal durations for each intersection.

3. Simulating Traffic Data
c
Copy
Edit
TrafficData get_traffic_data(int intersection_id) {
    TrafficData data;
    data.traffic_level = rand() % MAX_TRAFFIC_LEVEL;
    data.pedestrian_count = rand() % 50;
    return data;
}
Simulates real-time data for a given intersection.
Uses random values to create traffic scenarios.

4. Adjusting Signal Timing
c
Copy
Edit
SignalTiming adjust_signal_timing(TrafficData data)
This function sets signal durations based on traffic conditions using simple AI logic:
If traffic is heavy (>70):
Green: 60s, Red: 30s (favor vehicle flow).
If moderate (40–70):
Green: 45s, Red: 45s (balanced).
If light (<40):
Green: 30s, Red: 60s (less vehicle priority).
Extra logic: If many pedestrians (>20) and low traffic (<40):
Shorten green by 10s, increase red by 10s (favor pedestrians).

5. Main Function Execution
c
Copy
Edit
int main() {
    srand(time(NULL));
Seeds the random number generator to get different outputs on each run.
c
Copy
Edit
    TrafficData traffic_data[MAX_INTERSECTIONS];
    SignalTiming signal_timing[MAX_INTERSECTIONS];
Arrays to store data for all intersections.
c
Copy
Edit
    for (int i = 0; i < MAX_INTERSECTIONS; i++) {
        traffic_data[i] = get_traffic_data(i);
        signal_timing[i] = adjust_signal_timing(traffic_data[i]);

        printf("Intersection %d:\n", i + 1);
        printf("  Traffic Level: %d\n", traffic_data[i].traffic_level);
        printf("  Pedestrian Count: %d\n", traffic_data[i].pedestrian_count);
        printf("  Green Time: %d seconds\n", signal_timing[i].green_time);
        printf("  Red Time: %d seconds\n\n", signal_timing[i].red_time);
    }
Loops through each intersection:
Gets simulated traffic data.
Adjusts signal timings.
Prints results to the console.

🧠 Concepts Demonstrated
Basic AI logic with condition-based decision making.
Random simulation to mimic real-world variability.
Use of structs for organizing data.
Modular function-based design.
Let me know if you'd like a visual flowchart of the logic or if you want to extend the program (e.g., adding yellow light, saving output, simulating over time, etc.)












# traffic-management
