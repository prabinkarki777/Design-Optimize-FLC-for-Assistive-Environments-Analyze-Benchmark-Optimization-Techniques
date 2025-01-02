### Design and Optimization of FLC for Intelligent Assistive Environments and Comparative Analysis of Benchmark Optimization Techniques with Genetic Algorithm and Particle Swarm Optimization


This repository provides a robust implementation of a smart fuzzy logic controller (FLC) integrated with Genetic Algorithm (GA) and Particle Swarm Optimization (PSO) for optimizing fuzzy membership functions and control rules. The system is designed to manage environmental factors such as temperature, air quality, and daylight illumination, making it suitable for applications like smart home automation.

## Features

1. **Fuzzy Logic Controller (FLC):**
   - Models environmental parameters like temperature, air quality, and daylight illumination.
   - Configurable membership functions for linguistic variables.
   - Rule-based decision-making for controlling heater, air purifier, and illuminance control.

2. **Optimization using Genetic Algorithm (GA):**
   - Optimizes membership function parameters.
   - Uses mutation, crossover, and selection techniques.
   - Tracks fitness convergence over generations.

3. **Optimization using Particle Swarm Optimization (PSO):**
   - Employs swarm-based search for global optimization.
   - Tracks the best solution and convergence across iterations.

4. **Benchmark Functions:**
   - Includes Shifted Schwefel's Problem with Noise in Fitness and Shifted Rastrigin's Function for testing.

## Getting Started

### Prerequisites

- Python 3.7+
- Required Libraries:
  ```bash
  pip install numpy matplotlib scikit-fuzzy
  ```

### Installation

Clone the repository:
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

### Running the Fuzzy Logic Controller

#### Configure the FLC:

The `configure_fuzzy_logic` function initializes the fuzzy controller with membership functions derived from the chromosome parameters. Example:

```python
chromosome = np.random.uniform(0, 100, 69)  # Example chromosome
flc = configure_fuzzy_logic(chromosome)
```

#### Compute Outputs:

Provide environmental inputs and compute the controller's outputs:

```python
heater, air_purifier, illuminance_control, uncovered = compute_outputs(
    temperature=25, air_quality=150, daylight_illumination=50, flc=flc
)
```

### Optimization Using Genetic Algorithm (GA)

#### Run the GA Optimization:

```python
population = initialize_population(pop_size=50, chromosome_length=69)
for generation in range(500):
    fitnesses = [fitness_function(ind, dataset) for ind in population]
    population = evolve_population(population, fitnesses)
```

#### Plot Convergence:

```python
plt.plot(range(len(fitness_over_generations)), fitness_over_generations)
plt.title("Fitness Over Generations")
plt.xlabel("Generation")
plt.ylabel("Fitness")
plt.show()
```

### Optimization Using Particle Swarm Optimization (PSO)

#### Run the PSO Optimization:

```python
best_fitness, convergence = particle_swarm_optimization(
    func=shifted_rastrigin,
    o=o_shifted,
    bounds=(-5, 5),
    dims=10,
    iterations=100,
    swarm_size=50
)
```

#### Plot Convergence:

```python
plt.plot(convergence)
plt.title("PSO Convergence")
plt.xlabel("Iteration")
plt.ylabel("Fitness")
plt.show()
```

### Benchmarking

Use the provided benchmark functions to test optimization algorithms:

```python
shifted_schwefel(x, o)
shifted_rastrigin(x, o)
```

## Results

- **Fuzzy Controller:**
  - Achieves effective control of heater, air purifier, and illuminance.
  - Visualizes membership functions and simulation outputs.

- **GA Optimization:**
  - Demonstrates fitness improvement across generations.
  - Optimizes fuzzy parameters for minimum error.

- **PSO Optimization:**
  - Efficiently finds global optima.
  - Displays fitness convergence over iterations.

## Visualizations

### Membership Functions:

```python
plot_all_membership_functions(fuzzy_variables)
```

### Control Surfaces:

```python
generate_all_control_surfaces_in_one_figure(flc, inputs, outputs, ranges)
```

## Future Enhancements

1. Extend fuzzy rules for additional environmental scenarios.
2. Explore hybrid GA-PSO optimization techniques.
3. Integrate with real-world IoT systems for live testing.

